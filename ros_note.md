## some note from tf tutorials
* 发布静态tf变换时，使用头文件```#include <tf2_ros/static_transform_broadcaster.h>```，使用其中的staticTransformBroadcaster类型（定义对象时添加static关键字？），并且只需要发送一次坐标变换即可一直存在。**注意：必须都加上static关键字，不然无法查询到/tf话题**
* 发布动态tf变换需要一直发送，不然无法一直lookup到。

**使用geometry_msgs::Quaternion和tf2::Quaternion的区别**
* 前者可以直接赋给TF.transform.rotation，后者则是逐一使用成员函数返回四元素的值。
* 两者创建四元素的方法不同
> ```
	geometry_msgs::Quaternion q;
	q.create...
	tf2::Quaternion q2;
	q2.setRPY(roll,pitch,yaw);
```
	

