> **博主介绍：**
> 本人专注于Android/java/数据库/微信小程序技术领域的开发，以及有好几年的计算机毕业设计方面的实战开发经验和技术积累；尤其是在安卓（Android）的app的开发和微信小程序的开发，很是熟悉和了解；本人也是多年的Android开发人员；希望我发布的此篇文件可以帮助到您；
>
> 🍅 **文章末尾获取源码下载方式** 🍅

#### **功能演示**

**详情演示视频请文字末尾公众号咨询，我会发给您；**

##### 1：后台演示

![](./res/6b9522f7d4974fd3b439de370e6bfc19.gif)

##### 2：客户端演示

![](./res/42c09aa26523467f8ca0fd12461b31bf.gif)

#### 一、项目介绍

> 该系统主要功能模块如下所述：
>
> （1）登录与注册
>
>
> 以不同的身份登录app权限不同，点开app后，首先进入的是登录界面,用户在登录界面选择身份，学生可输入用户名和密码进行登录，教师需要进行注册，通过注册的用户名和密码进行登录。未注册的用户输入用户名密码，则无法登录，可跳转到注册页面或者退出，点击登录后，将对用户名密码与数据库进行比对，一致则登录成功，进入系统主界面，否则，提示登录失败，需要重新登录。
>
> （2）查看随堂测验成绩模块
>
>
> 该模块是用来对学生进行随堂测验成绩记录。点击随堂测验功能，首先需判断用户身份，如果是学生，只能进行查看随堂测验的成绩，若当前没有录入随堂测验成绩，则显示当前无成绩。如果是任课老师或者管理员则可以进行录入成绩和查看成绩。
>
> （3）低分预警模块
>
> 该模块是对考勤成绩低于老师设定值的同学，自动通知老师及学生本人。注：老师将设置首次预警分数，第二次预警分数，第三次预警分数。
>
> （4）计算出总评成绩模块
>
>
> 该模块是计算出该门课程的总评成绩。总评成绩是由平时成绩、期中成绩、实验成绩、期末成绩组成。系统应能对实验成绩、期中期末成绩进行录入，从数据库中提取平时成绩，老师进行设置成绩比例，然后自动计算出总评成绩。注：该模块只能是任课老师或者管理员进行设置比例，录入成绩，学生只能进行查看成绩。
>
> （5）自动汇总功能模块
>
>
> 该模块用于显示平时成绩。系统将按照设定的比例，自动汇总平时成绩最终结果。学生可以随时查看自己当前的平时成绩结果和排名。任课教师也可进行调整比例，进行平时成绩的调整。
>
> （6）考勤统计功能模块
>
>
> 该模块是对课堂考勤情况进行记录。点击考勤统计功能，跳转至考勤统计功能页面，在这将所有同学默认为全勤的状态，如有同学缺勤，迟到，请假等情况，则可以通过找到该同学的信息，进行修改，或者利用搜索框搜索，然后进行修改。注：学生只能查看记录，不可以修改记录。
>
> （7）课堂记录功能模块
>
>
> 该模块用于对课堂违纪情况进行记录。由管理员或者任课老师进行对本班的课程，某节课的违纪情况进行记录。学生可以查看自己是否有违纪情况，若有疑问，可以向系统提交反馈信息。还需加上“其他”选项，以便手动输入违纪的情况。

#### 二、运行环境

> 1：客户端使用Android stuido进行开发；  
>  2：服务端后台使用Myeclipse2014进行开发；  
>  3：mysql数据库进行数据存储；  
>  4：需要jdk1.7以上  
>  5：使用雷电模拟器或者Androidstuio自带的模拟器进行运行

#### 三、使用技术

> **总体设计逻辑和思路：**  
>  1：先设计数据库表文件  
>  2：写服务端jsp页面以及写api接口给客户端提供数据  
>  3：完成后台服务端的数据交互，也就是jsp页面数据的存储和显示  
>  4：进行客户端页面的开发；  
>  5：进行客户端对api接口的调用，也就是获取数据库的数据以及在客户端进行显示
>
> **移动端：**  
>  1：使用android原生控件以及xml布局文件来完成界面的显示  
>  2：使用java代码完成功能的数据和逻辑交互  
>  3：使用http网络请求完成数据的请求；  
>  **4：使用json数据解析完成客户端数据的回调和显示**
>
> **服务端后台：**  
>  1：使用mysql完成数据的存储  
>  2：使用jdbc完成数据库和代码的逻辑交互  
>  3：使用jsp完成网页数据的显示  
>  4：使用java代码完成api接口的编写以及以及数据的回调

#### 四、数据库设计

    
    
    /*
    Navicat MySQL Data Transfer
    
    Source Server         : mydb
    Source Server Version : 50528
    Source Host           : localhost:3306
    Source Database       : studyscoredb
    
    Target Server Type    : MYSQL
    Target Server Version : 50528
    File Encoding         : 65001
    
    Date: 2022-01-01 21:22:00
    */
    
    SET FOREIGN_KEY_CHECKS=0;
    
    -- ----------------------------
    -- Table structure for attendancetb
    -- ----------------------------
    DROP TABLE IF EXISTS `attendancetb`;
    CREATE TABLE `attendancetb` (
      `attendanceId` int(11) NOT NULL AUTO_INCREMENT,
      `attendanceCourseId` int(11) DEFAULT NULL,
      `attendanceCourseName` varchar(255) DEFAULT NULL,
      `attendanceType` varchar(255) DEFAULT NULL,
      `attendanceStuId` int(11) DEFAULT NULL,
      `attendanceStuName` varchar(255) DEFAULT NULL,
      `attendanceDate` varchar(100) DEFAULT NULL,
      PRIMARY KEY (`attendanceId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of attendancetb
    -- ----------------------------
    INSERT INTO `attendancetb` VALUES ('1', '10', '英语', '缺勤', '90', 'Tomcat', '2022-01-01');
    INSERT INTO `attendancetb` VALUES ('2', '10', '英语', '请假', '91', 'jackmao', '2022-01-01');
    INSERT INTO `attendancetb` VALUES ('3', '10', '英语', '迟到', '93', '哲老师', '2022-01-01');
    INSERT INTO `attendancetb` VALUES ('4', '10', '英语', '迟到', '94', '小哲理', '2022-01-01');
    
    -- ----------------------------
    -- Table structure for proportiontb
    -- ----------------------------
    DROP TABLE IF EXISTS `proportiontb`;
    CREATE TABLE `proportiontb` (
      `proportionId` int(11) NOT NULL AUTO_INCREMENT,
      `proportionOne` varchar(255) DEFAULT NULL,
      `proportionTwo` varchar(255) DEFAULT NULL,
      `proportionThree` varchar(255) DEFAULT NULL,
      `proportionFour` varchar(255) DEFAULT NULL,
      PRIMARY KEY (`proportionId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of proportiontb
    -- ----------------------------
    INSERT INTO `proportiontb` VALUES ('2', '10', '10', '40', '40');
    
    -- ----------------------------
    -- Table structure for scoretb
    -- ----------------------------
    DROP TABLE IF EXISTS `scoretb`;
    CREATE TABLE `scoretb` (
      `scoreId` int(50) NOT NULL AUTO_INCREMENT,
      `scoreType` varchar(255) DEFAULT NULL,
      `scoreStuId` varchar(255) DEFAULT NULL,
      `scoreStuName` varchar(255) DEFAULT NULL,
      `scoreCourseId` varchar(255) DEFAULT NULL,
      `scoreMessage` varchar(255) DEFAULT NULL,
      `scoreUserId` varchar(11) DEFAULT NULL,
      `scoreUserName` varchar(255) DEFAULT NULL,
      `scoreCreatime` varchar(100) DEFAULT NULL,
      PRIMARY KEY (`scoreId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=23 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of scoretb
    -- ----------------------------
    INSERT INTO `scoretb` VALUES ('14', '2021-12-31随堂测验', '90', 'Tomcat', '10', '30', '88', '王老师', '2022-01-01 13:47');
    INSERT INTO `scoretb` VALUES ('15', '期中成绩', '90', 'Tomcat', '10', '88', '88', '王老师', '2022-01-01 13:48');
    INSERT INTO `scoretb` VALUES ('16', '期末成绩', '90', 'Tomcat', '10', '99', '88', '王老师', '2022-01-01 13:48');
    INSERT INTO `scoretb` VALUES ('17', '2022-01-01随堂测验', '91', 'jackmao', '10', '56', '88', '王老师', '2022-01-01 13:53');
    INSERT INTO `scoretb` VALUES ('18', '2022-01-01随堂测验', '92', 'duoduo1028', '10', '89', '88', '王老师', '2022-01-01 13:53');
    INSERT INTO `scoretb` VALUES ('19', '期中成绩', '93', '哲老师', '10', '150', '88', '王老师', '2022-01-01 14:07');
    INSERT INTO `scoretb` VALUES ('20', '2022-01-01随堂测验', '93', '哲老师', '10', '6.0', '88', '王老师', '2022-01-01 19:02');
    INSERT INTO `scoretb` VALUES ('21', '2022-01-01实验成绩', '90', '学生tom', '10', '9.9', '88', '王老师', '2022-01-01 21:16');
    INSERT INTO `scoretb` VALUES ('22', '期中成绩', '93', '哲老师', '10', '35.2', '88', '王老师', '2022-01-01 21:17');
    
    -- ----------------------------
    -- Table structure for token
    -- ----------------------------
    DROP TABLE IF EXISTS `token`;
    CREATE TABLE `token` (
      `tid` int(100) NOT NULL AUTO_INCREMENT,
      `uid` varchar(100) CHARACTER SET utf8 NOT NULL,
      `utoken` varchar(500) CHARACTER SET utf8 NOT NULL,
      PRIMARY KEY (`tid`)
    ) ENGINE=InnoDB AUTO_INCREMENT=119 DEFAULT CHARSET=latin1;
    
    -- ----------------------------
    -- Records of token
    -- ----------------------------
    INSERT INTO `token` VALUES ('114', '88', 'CWYQpnKHA8IrG07bRBnYPjD73K3+3uRZGpOSjlb+djzTjCzhhIKUP2LX4XmUxsOzmBAEIFM2hwBBoI2bW00tFg==');
    INSERT INTO `token` VALUES ('115', '89', 'fQu2I17XIcBC/5UnSh9tmyvwBvuqr97RjQi5uLqItZQHbQeOQtvD7krqehqA4HcJdHBtHXsK1Nb4qW5FoOzRkw==');
    INSERT INTO `token` VALUES ('116', '90', 'SIaSaIKjHtlzWN8OHYArfCvwBvuqr97RjQi5uLqItZQHbQeOQtvD7lDnwz/G8Ma9R27fbsk8oS34qW5FoOzRkw==');
    INSERT INTO `token` VALUES ('117', '91', 'glROHWaqqwd0+Q+ZWmo2CCvwBvuqr97RjQi5uLqItZQHbQeOQtvD7gOVgk0Xa0UoOj43tCmRiKj4qW5FoOzRkw==');
    INSERT INTO `token` VALUES ('118', '92', '4LstZGuk9RUW4kjNTo/n5DD73K3+3uRZGpOSjlb+djzTjCzhhIKUP41AxGCz8s6uYsPfM6nhL1hBoI2bW00tFg==');
    
    -- ----------------------------
    -- Table structure for topicvideotb
    -- ----------------------------
    DROP TABLE IF EXISTS `topicvideotb`;
    CREATE TABLE `topicvideotb` (
      `topicvideoId` int(11) NOT NULL AUTO_INCREMENT,
      `topicvXueQi` varchar(255) DEFAULT NULL,
      `topicvideoUserId` int(11) DEFAULT NULL,
      `topicvideoUserName` varchar(255) DEFAULT NULL,
      `topicvideoName` varchar(255) DEFAULT NULL,
      `topicvideoFile` varchar(255) DEFAULT NULL,
      `topicvideoTime` varchar(100) DEFAULT NULL,
      `topicvideoState` varchar(255) DEFAULT NULL,
      PRIMARY KEY (`topicvideoId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=19 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of topicvideotb
    -- ----------------------------
    INSERT INTO `topicvideotb` VALUES ('10', '大一上学期', '88', '王老师', '英语', '一号教学楼1001', '2022-01-01 13:48', '1');
    INSERT INTO `topicvideotb` VALUES ('11', '大二上学期', '88', '王老师', '计算机基础', '一号教学楼1001', '2022-01-01 13:48', '1');
    INSERT INTO `topicvideotb` VALUES ('12', '大三上学期', '88', '王老师', 'android', '一号教学楼', '2022-01-01 13:48', '1');
    INSERT INTO `topicvideotb` VALUES ('13', '大四上学期', '88', '王老师', 'mysql', '一号教学楼', '2022-01-01 13:48', '1');
    INSERT INTO `topicvideotb` VALUES ('14', '大一下学期', '93', '哲老师', 'mysql基础', '一号教学楼1001', '2022-01-01 13:48', '1');
    
    -- ----------------------------
    -- Table structure for user
    -- ----------------------------
    DROP TABLE IF EXISTS `user`;
    CREATE TABLE `user` (
      `uid` int(255) NOT NULL AUTO_INCREMENT,
      `uname` varchar(200) CHARACTER SET utf8 NOT NULL,
      `uphone` varchar(100) CHARACTER SET utf8 NOT NULL,
      `upswd` varchar(200) CHARACTER SET utf8 NOT NULL,
      `utime` varchar(300) CHARACTER SET utf8 NOT NULL,
      `utype` varchar(255) CHARACTER SET utf8 DEFAULT NULL,
      `uflag` varchar(255) DEFAULT NULL,
      PRIMARY KEY (`uid`)
    ) ENGINE=InnoDB AUTO_INCREMENT=96 DEFAULT CHARSET=latin1;
    
    -- ----------------------------
    -- Records of user
    -- ----------------------------
    INSERT INTO `user` VALUES ('88', '王老师', '15249241001', '123456', '2022-01-01 13:48', '2', '1');
    INSERT INTO `user` VALUES ('90', '学生tom', '15249242001', '123456', '2022-01-01 13:48', '1', '1');
    INSERT INTO `user` VALUES ('91', 'jackmao', '15249242006', '123456', '2022-01-01 13:48', '1', '1');
    INSERT INTO `user` VALUES ('92', 'duoduo1028', '15249242006', '123456', '2022-01-01 13:48', '1', '1');
    INSERT INTO `user` VALUES ('93', '哲老师', '15388881001', '123456', '2022-01-01 13:48', '1', '1');
    INSERT INTO `user` VALUES ('94', '小哲理', '15288883001', '123456', '2022-01-01 13:48', '1', '1');
    INSERT INTO `user` VALUES ('95', '王主任', '15255551001', '123456', '2022-01-01 13:48', '3', '1');
    
    -- ----------------------------
    -- Table structure for violationtb
    -- ----------------------------
    DROP TABLE IF EXISTS `violationtb`;
    CREATE TABLE `violationtb` (
      `violationId` int(11) NOT NULL AUTO_INCREMENT,
      `violationCourseId` int(11) DEFAULT NULL,
      `violationCourseName` varchar(255) DEFAULT NULL,
      `violationStuId` int(11) DEFAULT NULL,
      `violationStuName` varchar(255) DEFAULT NULL,
      `violationMsg` varchar(255) DEFAULT NULL,
      `violationDate` varchar(100) DEFAULT NULL,
      PRIMARY KEY (`violationId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of violationtb
    -- ----------------------------
    INSERT INTO `violationtb` VALUES ('2', '10', '英语', '92', 'duoduo1028', '不好好上课，上课睡觉', '2022-01-01');
    INSERT INTO `violationtb` VALUES ('3', '10', '英语', '92', 'duoduo1028', '不好好上课，上课睡觉8888888', '2022-01-01');
    INSERT INTO `violationtb` VALUES ('4', '10', '英语', '94', '小哲理', '上课玩手机', '2022-01-01');
    
    -- ----------------------------
    -- Table structure for warningtb
    -- ----------------------------
    DROP TABLE IF EXISTS `warningtb`;
    CREATE TABLE `warningtb` (
      `warningId` int(11) NOT NULL AUTO_INCREMENT,
      `warningOne` varchar(255) DEFAULT NULL,
      `warningTwo` varchar(255) DEFAULT NULL,
      `warningThree` varchar(255) DEFAULT NULL,
      PRIMARY KEY (`warningId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of warningtb
    -- ----------------------------
    INSERT INTO `warningtb` VALUES ('1', '60', '65', '70');
    INSERT INTO `warningtb` VALUES ('2', '45', '65', '70');
    

#### 五、部分代码

#### 六、浏览更多Android毕业设计

[毕业设计-基于android的租房信息发布平台的APP_信息发布app源码_Android毕业设计源码的博客-
CSDN博客](https://blog.csdn.net/u014388322/article/details/100656450?spm=1001.2014.3001.5502
"毕业设计-基于android的租房信息发布平台的APP_信息发布app源码_Android毕业设计源码的博客-CSDN博客")

[毕业设计-基于android选课系统的设计与实现_android学生选课系统_Android毕业设计源码的博客-
CSDN博客](https://blog.csdn.net/u014388322/article/details/100656536?spm=1001.2014.3001.5502
"毕业设计-基于android选课系统的设计与实现_android学生选课系统_Android毕业设计源码的博客-CSDN博客")

[毕业设计之校园一卡通管理系统的设计与实现_一卡通管理系统实现_Android毕业设计源码的博客-
CSDN博客](https://blog.csdn.net/u014388322/article/details/126048550?spm=1001.2014.3001.5502
"毕业设计之校园一卡通管理系统的设计与实现_一卡通管理系统实现_Android毕业设计源码的博客-CSDN博客")

[基于Android的校园二手闲置物品交易系统设计与实现_基于android的二手交易平台_Android毕业设计源码的博客-
CSDN博客](https://blog.csdn.net/u014388322/article/details/128232475?spm=1001.2014.3001.5502
"基于Android的校园二手闲置物品交易系统设计与实现_基于android的二手交易平台_Android毕业设计源码的博客-CSDN博客")

[基于androidstudio校园快递APP系统的设计与实现_android studio论文_Android毕业设计源码的博客-
CSDN博客](https://blog.csdn.net/u014388322/article/details/128545390?spm=1001.2014.3001.5502
"基于androidstudio校园快递APP系统的设计与实现_android studio论文_Android毕业设计源码的博客-CSDN博客")

[基于android的商城购物定制APP_安卓开发购物app_Android毕业设计源码的博客-
CSDN博客](https://blog.csdn.net/u014388322/article/details/128746697?spm=1001.2014.3001.5502
"基于android的商城购物定制APP_安卓开发购物app_Android毕业设计源码的博客-CSDN博客")

> 更多毕业设计可以浏览我的个人主页哦！

#### 七、源码下载

> 大家 **点赞、收藏、关注、评论** 啦 、 **查看** 👇🏻👇🏻👇🏻 **获取联系方式** 👇🏻👇🏻👇🏻
>
> <https://download.csdn.net/download/u014388322/88192292>
>
> ​

