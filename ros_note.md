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


