> **博主介绍：**
> 本人专注于Android/java/数据库/微信小程序技术领域的开发，以及有好几年的计算机毕业设计方面的实战开发经验和技术积累；尤其是在安卓（Android）的app的开发和微信小程序的开发，很是熟悉和了解；本人也是多年的Android开发人员；希望我发布的此篇文件可以帮助到您；
>
> 🍅 **文章末尾获取源码下载方式** 🍅

**目录**

一、项目介绍

二、运行环境

三、使用技术

四、数据库设计

五、部分代码

1：我的订单代码

2：服务详情

六、浏览更多Android毕业设计

七、毕业设计部分免费源码分享下载

* * *

#### 一、项目介绍

> 客户端：
>
> 1：用户登录和注册模块：完成用户信息的登记
>
> 2：服务展示模块：用来展示家政人员的基本信息和服务详情；
>
> 3：预约模块：对感兴趣的家政人员进行预约
>
> 4：我的订单：可以查看自己的预约记录
>
> 5：个人信息：可以查看自己的个人信息，以及修改密码，添加自己的地址等；
>
> 服务端：
>
> 1：用户信息的管理
>
> 2：家政人员信息的管理和查看
>
> 3：订单信息的管理和审核
>
> 要求：仿照现有的APP--家政帮
>
> 首页实现功能：
>
> 1、菜单
>
> 2、轮播图（轮播图点击）（图片轮播）
>
> 3、地址
>
> 4、服务界面菜单：
>
> 1>具体的家政服务项目；
>
> 2>服务项目进入之后有相应的介绍以及下单
>
> 菜单页面实现的功能：
>
> 1、两种出现方式：侧滑出现与点击菜单按钮
>
> 2、进入菜单后，最上方是 注册/登录（右侧是头像）
>
> 3、下方是每一个菜单项
>
> 4、返回首页：侧滑隐藏菜单与点击返回按钮
>
> 地址界面的实现：
>
> 1、关键字联想地址
>
> 2、地址列表，可修改删除
>
> 3、地址保存
>
> 4、与菜单界面的地址相同
>
> 登录注册用邮件发送验证

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
    
    Source Server         : mydata
    Source Server Version : 50537
    Source Host           : localhost:3306
    Source Database       : houseworkdb
    
    Target Server Type    : MYSQL
    Target Server Version : 50537
    File Encoding         : 65001
    
    Date: 2019-01-14 17:51:03
    */
    
    SET FOREIGN_KEY_CHECKS=0;
    
    -- ----------------------------
    -- Table structure for address
    -- ----------------------------
    DROP TABLE IF EXISTS `address`;
    CREATE TABLE `address` (
      `addressId` int(50) NOT NULL AUTO_INCREMENT,
      `addressHouse` varchar(300) NOT NULL,
      `addressNo` varchar(100) DEFAULT NULL,
      `addressUserName` varchar(255) DEFAULT NULL,
      `addressUserPhone` varchar(255) DEFAULT NULL,
      `addressUserId` varchar(100) DEFAULT NULL,
      PRIMARY KEY (`addressId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=18 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of address
    -- ----------------------------
    INSERT INTO `address` VALUES ('14', '多多小区', '1002', 'pony', '102', '106');
    INSERT INTO `address` VALUES ('15', '66', '88', '88', '88', '106');
    INSERT INTO `address` VALUES ('16', '99', '99', '99', '99', '106');
    INSERT INTO `address` VALUES ('17', '多多小区', '1002', 'pony', '15249248989', '106');
    
    -- ----------------------------
    -- Table structure for advertisementtb
    -- ----------------------------
    DROP TABLE IF EXISTS `advertisementtb`;
    CREATE TABLE `advertisementtb` (
      `advertisementId` int(50) NOT NULL AUTO_INCREMENT,
      `advertisementName` varchar(255) DEFAULT NULL,
      `advertisementMessage` varchar(1500) DEFAULT NULL,
      `advertisementTime` varchar(100) DEFAULT NULL,
      `advertisementImg` varchar(255) DEFAULT NULL,
      PRIMARY KEY (`advertisementId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=11 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of advertisementtb
    -- ----------------------------
    INSERT INTO `advertisementtb` VALUES ('9', '西安濯缨家政服务有限公司', '从事各类保洁服务，服务范围广，服务质量优，从业以来，受到广大消费者和业内人士的好评。因为我们服务跨度大，服务要求的不同，我不断总结经验，已经制定出了一套完善的服务体系，保质保量的前提下，较大限度的节约时间。', '2018-12-12 10:11:44', 'dota_5.jpg');
    INSERT INTO `advertisementtb` VALUES ('10', '单位开荒保洁', '本公司拥有一套完善的管理机制，实行公司员工管理制，对月嫂的服务进行全程监督和指导，月嫂上岗有本公司开具的上岗单及客户对服务人员的点评回执单。本公司拥有一套完善的管理机制，实行公司员工管理制，对月嫂的服务进行全程监督和指导，月嫂上岗有本公司开具的上岗单及客户对服务人员的点评回执单。', '2018-12-12 10:12:41', 'dota_6.jpg');
    
    -- ----------------------------
    -- Table structure for ordermsg
    -- ----------------------------
    DROP TABLE IF EXISTS `ordermsg`;
    CREATE TABLE `ordermsg` (
      `orderId` int(50) NOT NULL AUTO_INCREMENT,
      `orderMessageId` varchar(50) DEFAULT NULL,
      `orderMessageName` varchar(255) DEFAULT NULL,
      `orderMessageMoney` varchar(255) DEFAULT NULL,
      `orderUserId` varchar(100) DEFAULT NULL,
      `orderUserName` varchar(255) DEFAULT NULL,
      `orderTime` varchar(100) DEFAULT NULL,
      PRIMARY KEY (`orderId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=9 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of ordermsg
    -- ----------------------------
    INSERT INTO `ordermsg` VALUES ('6', '3', '清洗油烟机', '500', '106', '小丸子', '2018-12-15 01:04');
    INSERT INTO `ordermsg` VALUES ('7', '2', '清洗玻璃', '500', '106', '小丸子', '2018-12-15 01:04');
    INSERT INTO `ordermsg` VALUES ('8', '1', '房间打扫', '300', '106', '小丸子', '2018-12-15 01:16');
    
    -- ----------------------------
    -- Table structure for review
    -- ----------------------------
    DROP TABLE IF EXISTS `review`;
    CREATE TABLE `review` (
      `rId` int(50) NOT NULL AUTO_INCREMENT,
      `rUserId` varchar(50) NOT NULL,
      `rUserName` varchar(100) NOT NULL,
      `rWeiBoId` varchar(100) NOT NULL,
      `rReviewContent` varchar(300) NOT NULL,
      `rCreatime` varchar(100) NOT NULL,
      PRIMARY KEY (`rId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=48 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of review
    -- ----------------------------
    INSERT INTO `review` VALUES ('45', '29', 'Tom', '5', '我我摸', '2017-03-15 11:19');
    INSERT INTO `review` VALUES ('46', '29', 'Tom', '5', '我OK咯', '2017-03-15 11:56');
    INSERT INTO `review` VALUES ('47', '35', 'pony1116', '10', '谢谢你的服务，对你很满意', '2017-03-15 14:15');
    
    -- ----------------------------
    -- Table structure for servicetb
    -- ----------------------------
    DROP TABLE IF EXISTS `servicetb`;
    CREATE TABLE `servicetb` (
      `serviceId` int(11) NOT NULL AUTO_INCREMENT,
      `serviceName` varchar(255) DEFAULT NULL,
      `serviceTypeId` varchar(100) DEFAULT NULL,
      `serviceTypeName` varchar(255) DEFAULT NULL,
      `serviceMoney` varchar(255) DEFAULT NULL,
      `serviceUserName` varchar(255) DEFAULT NULL,
      `serviceUserPhone` varchar(255) DEFAULT NULL,
      `serviceMessage` varchar(1500) DEFAULT NULL,
      `serviceTime` varchar(100) DEFAULT NULL,
      PRIMARY KEY (`serviceId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of servicetb
    -- ----------------------------
    INSERT INTO `servicetb` VALUES ('1', '房间打扫', '12', '打扫', '300', '王女士', '15249248888', '从事各类保洁服务，服务范围广，服务质量优，从业以来，受到广大消费者和业内人士的好评。因为我们服务跨度大，服务要求的不同，我不断总结经验，已经制定出了一套完善的服务体系，保质保量的前提下，较大限度的节约时间。', '2018-12-12 09:50');
    INSERT INTO `servicetb` VALUES ('2', '清洗玻璃', '12', '打扫', '500', '王女士', '15249248888', '从事各类保洁服务，服务范围广，服务质量优，从业以来，受到广大消费者和业内人士的好评。因为我们服务跨度大，服务要求的不同，我不断总结经验，已经制定出了一套完善的服务体系，保质保量的前提下，较大限度的节约时间。', '2018-12-12 09:57');
    INSERT INTO `servicetb` VALUES ('3', '清洗油烟机', '12', '打扫', '500', '王女士', '15249248888', '从事各类保洁服务，服务范围广，服务质量优，从业以来，受到广大消费者和业内人士的好评。因为我们服务跨度大，服务要求的不同，我不断总结经验，已经制定出了一套完善的服务体系，保质保量的前提下，较大限度的节约时间。', '2018-12-12 09:59');
    
    -- ----------------------------
    -- Table structure for typetb
    -- ----------------------------
    DROP TABLE IF EXISTS `typetb`;
    CREATE TABLE `typetb` (
      `typeId` int(50) NOT NULL AUTO_INCREMENT,
      `typeName` varchar(255) DEFAULT NULL,
      `typeTime` varchar(100) DEFAULT NULL,
      PRIMARY KEY (`typeId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=18 DEFAULT CHARSET=utf8;
    
    -- ----------------------------
    -- Records of typetb
    -- ----------------------------
    INSERT INTO `typetb` VALUES ('12', '打扫', '2018-12-12 09:21');
    INSERT INTO `typetb` VALUES ('13', '买菜', '2018-12-12 09:19');
    INSERT INTO `typetb` VALUES ('14', '做饭', '2018-12-12 09:19');
    INSERT INTO `typetb` VALUES ('15', '家庭保洁', '2018-12-12 09:20');
    INSERT INTO `typetb` VALUES ('16', '母婴服务', '2018-12-12 09:20');
    INSERT INTO `typetb` VALUES ('17', '物品维修', '2018-12-12 09:20');
    
    -- ----------------------------
    -- Table structure for user
    -- ----------------------------
    DROP TABLE IF EXISTS `user`;
    CREATE TABLE `user` (
      `userId` int(255) NOT NULL AUTO_INCREMENT,
      `userName` varchar(200) CHARACTER SET utf8 NOT NULL,
      `userPhone` varchar(100) CHARACTER SET utf8 NOT NULL,
      `userPswd` varchar(200) CHARACTER SET utf8 NOT NULL,
      `userAddress` varchar(255) CHARACTER SET utf8 DEFAULT NULL,
      `userTime` varchar(300) CHARACTER SET utf8 NOT NULL,
      PRIMARY KEY (`userId`)
    ) ENGINE=InnoDB AUTO_INCREMENT=112 DEFAULT CHARSET=latin1;
    
    -- ----------------------------
    -- Records of user
    -- ----------------------------
    INSERT INTO `user` VALUES ('106', '小丸子', '15249243002', '123456', '多多小区1002', '2018-12-12 17:03');
    INSERT INTO `user` VALUES ('109', '小李子', '15249247878', '123456', null, '2018-12-13 16:15');
    

#### 五、部分代码

##### 1：我的订单代码

    
    
    public class ServiceListActivity extends BaseActivity  {
    
    	// 标题
    	private TextView mTvTitle;
    	// 返回
    	private ImageView mIvBack;
    	private TextView mIvStu;
    	private ListView mListMessage;
    	private List<ServiceModel> list_result = new ArrayList<ServiceModel>();
    	private String state;
    	private LinearLayout mllNomessage;
    	ServiceListListAdapter orderListAdapter;
    	
    	private TypeModel typeModel;
    
    	@Override
    	protected void onCreate(Bundle savedInstanceState) {
    		super.onCreate(savedInstanceState);
    		setContentView(R.layout.activity_im);
    	
    	}
    
    	@Override
    	protected void onResume() {
    		super.onResume();
    		initWidget();
    		initData();
    	}
    	
    	
    	@Override
    	public void onClick(View v) {
    		switch (v.getId()) {
    		case R.id.mIvBack:
    			finish();
    			break;
    		}
    	}
    
    	@Override
    	public void initWidget() {
    		
    		typeModel = (TypeModel)this.getIntent().getSerializableExtra("msg");
    		
    		mIvStu = (TextView) findViewById(R.id.mIvStu);
    		mIvStu.setText("添加");
    		mIvStu.setVisibility(View.GONE);
    		mllNomessage = (LinearLayout) findViewById(R.id.mllNomessage);
    		mListMessage = (ListView) findViewById(R.id.mListMessage);
    
    		mIvBack = (ImageView) findViewById(R.id.mIvBack);
    		mTvTitle = (TextView) findViewById(R.id.mTvTitle);
    		state = this.getIntent().getStringExtra("state");
    		mTvTitle.setText("我的订单");
    		mIvBack.setVisibility(View.VISIBLE);
    		mIvBack.setOnClickListener(this);
    		mIvStu.setOnClickListener(this);
    	}
    
    	@Override
    	public void initData() {
    		listServicePhoneMessage(true);
    
    		
    		
    
    		mListMessage.setOnItemClickListener(new OnItemClickListener() {
    
    			@Override
    			public void onItemClick(AdapterView<?> arg0, View arg1, int position, long arg3) {
    				Intent intent = new Intent(ServiceListActivity.this, ServiceMessageActivity.class);
    				intent.putExtra("msg", list_result.get(position));
    				startActivity(intent);
    			}
    		});
    	}
    
    	private void listServicePhoneMessage(boolean isShow) {
    		AjaxParams params = new AjaxParams();
    		params.put("action_flag", "listServicePhoneMessage");
    		params.put("serviceTypeId", typeModel.getTypeId());
    		httpPost(Consts.URL + Consts.APP.MessageAction, params, Consts.actionId.resultFlag, isShow, "正在加载...");
    	}
    
    
    	@Override
    	protected void callBackSuccess(ResponseEntry entry, int actionId) {
    		super.callBackSuccess(entry, actionId);
    
    		switch (actionId) {
    		case Consts.actionId.resultFlag:
    			if (null != entry.getData() && !TextUtils.isEmpty(entry.getData())) {
    
    				String jsonMsg = entry.getData().substring(1, entry.getData().length() - 1);
    				if (null != jsonMsg && !TextUtils.isEmpty(jsonMsg)) {
    					list_result = mGson.fromJson(entry.getData(), new TypeToken<List<ServiceModel>>() {
    					}.getType());
    					orderListAdapter = new ServiceListListAdapter(ServiceListActivity.this, list_result);
    					mListMessage.setAdapter(orderListAdapter);
    				} else {
    					mllNomessage.setVisibility(View.VISIBLE);
    				}
    			}
    			break;
    
    		default:
    			break;
    		}
    
    	}
    
    }
    

##### 2：服务详情

    
    
    public class ServiceMessageActivity extends BaseActivity {
    	// title
    	private TextView mTvTitle;
    	// 返回
    	private ImageView mIvBack;
    	// 查询按钮
    	private TextView mtvShowtitle;
    	
    	ServiceModel serviceModel;
    
    	private Button mbtnPay;
    
    	
    	private TextView mtvMsgOne;
    	private TextView mtvMsgTwo;
    	private TextView mtvMsgThree;
    	private TextView mtvMsgFour;
    	private TextView mtvcontent;
    	private TextView mtvMoney;
    	
    	
    	
    	@Override
    	protected void onCreate(Bundle savedInstanceState) {
    		super.onCreate(savedInstanceState);
    		setContentView(R.layout.activity_linesmsg);
    		initWidget();
    		initData();
    	}
    
    	@Override
    	public void initWidget() {
    
    		
    		
    		mtvMsgOne = (TextView) findViewById(R.id.mtvMsgOne);
    		mtvMsgTwo = (TextView) findViewById(R.id.mtvMsgTwo);
    		mtvMsgThree = (TextView) findViewById(R.id.mtvMsgThree);
    		mtvMsgFour = (TextView) findViewById(R.id.mtvMsgFour);
    		mtvcontent = (TextView) findViewById(R.id.mtvcontent);
    		mtvMoney = (TextView) findViewById(R.id.mtvMoney);
    		
    		mbtnPay = (Button) findViewById(R.id.mbtnPay);
    		mbtnPay.setOnClickListener(this);
    
    		mtvShowtitle = (TextView) findViewById(R.id.mtvtitle);
    		mtvcontent = (TextView) findViewById(R.id.mtvcontent);
    
    		mIvBack = (ImageView) findViewById(R.id.mIvBack);
    		mTvTitle = (TextView) findViewById(R.id.mTvTitle);
    		mTvTitle.setText("服务详情");
    		mIvBack.setVisibility(View.VISIBLE);
    		mIvBack.setOnClickListener(this);
    
    	}
    
    	@Override
    	public void onClick(View v) {
    
    		switch (v.getId()) {
    		case R.id.mIvBack:
    			ServiceMessageActivity.this.finish();
    			break;
    
    		case R.id.mbtnPay:
    			Intent mbtnPay = new Intent(this, PayMessageActivity.class);
    			mbtnPay.putExtra("msg", serviceModel);
    			startActivity(mbtnPay);
    			break;
    
    
    		}
    	}
    
    	@Override
    	public void initData() {
    		
    		mtvMsgOne = (TextView) findViewById(R.id.mtvMsgOne);
    		mtvMsgTwo = (TextView) findViewById(R.id.mtvMsgTwo);
    		mtvMsgThree = (TextView) findViewById(R.id.mtvMsgThree);
    		mtvMsgFour = (TextView) findViewById(R.id.mtvMsgFour);
    		mtvcontent = (TextView) findViewById(R.id.mtvcontent);
    		mtvMoney = (TextView) findViewById(R.id.mtvMoney);
    		
    	
    
    		serviceModel = (ServiceModel) this.getIntent().getSerializableExtra("msg");
    		mtvShowtitle.setText(serviceModel.getServiceName());
    		mtvMsgOne.setText("类型："+serviceModel.getServiceTypeName());
    		mtvMsgTwo.setText("价格："+serviceModel.getServiceMoney()+"元/次");
    		mtvMsgThree.setText("联系人："+serviceModel.getServiceUserName());
    		mtvMsgFour.setText("手机："+serviceModel.getServiceUserPhone());
    		mtvcontent.setText("        "+serviceModel.getServiceMessage());
    		mtvMoney.setText(serviceModel.getServiceMoney()+"元/次");
    		
    		// 书名，出版社，种类
    	}
    
    }
    

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

#### 七、毕业设计部分免费源码分享下载

> 大家 **点赞、收藏、关注、评论** 啦 、 **查看** 👇🏻👇🏻👇🏻 **获取联系方式** 👇🏻👇🏻👇🏻
>
> <https://download.csdn.net/download/u014388322/88180732>
>
> ​

