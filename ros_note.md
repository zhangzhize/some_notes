## some note from tf tutorials
* 发布静态tf变换时，使用头文件```#include <tf2_ros/static_transform_broadcaster.h>```，使用其中的staticTransformBroadcaster类型（定义对象时添加static关键字？），并且只需要发送一次坐标变换即可一直存在。**注意：必须都加上static关键字，不然无法查询到/tf话题**
* 发布动态tf变换需要一直发送，不然无法一直lookup到。

**使用geometry_msgs::Quaternion和tf2::Quaternion的区别**
* 前者可以直接赋给TF.transform.rotation，后者则是逐一使用成员函数返回四元素的值。
* 两者创建四元素的方法不同
```
geometry_msgs::Quaternion q;
q.create...
tf2::Quaternion q2;
q2.setRPY(roll,pitch,yaw);
```
	
## quaternion basic
* ros的四元素表示的顺序是(x,y,z,w)；而eigen四元素表示的顺序是(w,x,y,z).
* 不代表旋转的单位四元素是(0,0,0,1).
* 必须保证四元素的模长为1，可使用```q.normalize();```进行归一化
* ros中两种quaternion type的转换
```
#include <tf2_geometry_msgs/tf2_geometry_msgs.h>
tf2::Quaternion quat_tf;
geometry_msgs::Quaternion quat_msg=...;
//three methods
tf2::convert(quat_msg,quat_tf);
//or
tf2::fromMsg(quat_msg,quat_tf);
//或者反过来
quat_msg=tf2::toMsg(quat_tf);
```
	
**应用quaternion**
将四元素应用在姿态变换上，只需要将旧的四元素乘以代表旋转的四元素，**注意相乘的顺序很重要**
```
#include <tf2_geometry_msgs/tf2_geometry_msgs.h>
tf2::Quaternion q_orig,q_rot,q_new;
//get the original orientation of 'commanded_pose'
tf2::convert(commanded_pose.pose.orientation,q_orig);

double r=3.1159,p=0,y=0;
q_rot.setRPY(r,p,y);
q_new=q_rot*q_orig;
q_new.normalize();

//将新的四元素填回位姿，这需要转换为msg类型
tf2::convert(q_new,commanded_pose.pose.orientation);
```
	
**反转四元素**
反转四元素的简单方法是对w分量取反
```
q[3]=-q[3];
```
	
##相对旋转
如果有同一帧的两个四元素q1和q2，如果想找到**q1到q2的相对旋转qr**
```
//q2=qr*q1;
//qr=q2*q1.inverse
//c++示例
q1_inv[0]=q1[0];
q1_inv[1]=q1[1];
q1_inv[2]=q1[2];
q1_inv[3]=q1[3];
q2[0]=current_pose.orientation.x;
q2[1]=current_pose.orientation.y;
q2[2]=current_pose.orientation.z;
q2[3]=current_pose.orientation.w;
qr=q2*q1_inv;
```
	
## tf dubug
### 几种debug tf问题的策略
1. 搞清楚你想用tf干什么？
2. 在tf buffer中检查frame
2. 检查tf buffer的时间戳

**Finding the tf request**
在debug之前，需要知道
1. 需要监听的tf的两个坐标系的名称
2. 是哪个时间点的transform

[未理解1.2 'usingtransformPoint、transformVector，etc'](https://wiki.ros.org/tf/Troubleshooting)

* 检查fame
	* ```rosrun tf tf_echo frameA frameB```
	* ```rosrun tf2 tf2_echo frameA frameB```
	* ```rosrun tf view_frames | evince frames.pdf```
	* ```rosrun tf2_tools view_frames | evince frames.pdf```
* 检查时间戳
	* ```rosrun tf tf_monitor frameA frameB```
	* ```rosrun tf2 tf2_monitor frameA frameB```
	* 由于时间延迟，一般不能够查询到ros::Time::now()时间点的坐标变换
	* 出现too far in the past提示，注意tf只保持10s的buffer(可设置)

## 使用```tf2_ros::MessageFilter```处理stamped类型的数据
* tf2_ros::MessageFilter订阅任何带有header类型的msg，并将其缓存，直至可以将该msg数据转换到目标frame。
* example
```
std::string target_frame_="turtle1";
//tf
tf2_ros::Buffer buffer_;
tf2_ros::TransformListener tf2_(buffer_);
//pointStamped msg
ros::NodeHandle n_;
message_filters::Subscriber<geometry_msgs::PointStamped> point_sub_;
point_sub_.subscribe(n_,"turtle_point_frame_,10);
tf2_ros::MessageFilter<geometry_msgs::PointStamped> tf2_filter_(point_sub_,buffer_,target_frame_,10,0);
tf2_filter_.registerCallback(boost::bind(&msgCallback,this,_1));
//当到目标坐标系的tf变换可用时，进入回调函数 
//...buffer_.transform(...);
```
	
## [MessageFilter](http://wiki.ros.org/message_filters)
* message_filter是roscpp和rospy的一个应用库，集中了一些滤波算法中常用的一些消息。
* message_filter类似一个消息缓存，当消息到达消息过滤器时，可能并不会立即输出，而是在稍后的时间里**满足一定条件下输出**。
* 主要用法一：消息的订阅与回调
```
message_filters::Subscriber<std::msgs::Uint32> sub(nh,"my_topic",1);
sub.registerCallback(myCallback);
//等价于
ros::Subscriber sub=nh.subscribe("my_topic",1,myCallback);
```
* 主要用法之二：时间同步
**TimeSynchronizer**筛选器通过包含在header中的时间戳**同步进入的通道**，并以相同数量的通道的单个回调的形式输出他们。C++实现最多同步9个通道
```
message_filters::Subscriber<Imaga> image_sub(nh,"image",1);
message_filters::Subscriber<CameraInfo> info_sub(nh,"camera_info",1);
TimeSynchronizer<Image,CameraInfo> sync(image_sub,info_sub,10);
sync.registerCallback(boost::bind(&callback,_1,_2));
//...
```
	
* 主要用法之三：时间顺序的回调
**TimeSquencer**确保将小系统的时间戳**按时间顺序调用消息**。TimeSquencer具有特定的延迟，该延迟制定了在传递消息之前将消息排队的时间，在消息的时间戳**小于指定的延迟之前，永远不会调用消息的回调**。但是对于所有至少经过延迟过时的消息，将调用他们的回调并保证其按时间顺序排序。**如果消息是在消息以调用回调之前的某个时间到达的，则会将其丢弃。**
```
message_filters::Subscriber<std::msgs::String> sub(nh,"mytopic",1);
message_filters::TimeSequencer<std::msgs::String> seq(sub,ros::Duration(0.1),ros::Duration(0.01),10);
seq.registerCallback(myCallback);
```
