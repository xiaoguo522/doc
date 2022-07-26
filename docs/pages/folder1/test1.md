# 消息平台管理页面
## 1 说明
现有的消息平台管理页面没有针对实施与测试人员进行设计，太过于技术化，存在较高的使用门槛，亟须改进。

本文档只用于展示管理页面，不对技术细节进行说明。

## 2 应用管理
应用管理模板将项目中涉及到消息发送的应用，及消息发送所需要的配置信息进行统一维护。为每一类型的应用提供定制的配置管理页面，降低使用难度。

>目前，消息平台支持以下应用类型：  
* Android App
* iOS App
* 微信公众号
* 微信小程序
* 支付宝小程序  

>除以上类型外，消息平台还提供了两种虚拟应用类型：

* 跨平台应用：将不同类型的应用归为一类，便于进行数据统计与分析，如将医生端Android App，iOS App归为一类，或将患者端微信小程序，支付宝小程序归为一类。
* USER_SOURCE_ID：该类型应用互联网AppId为"USER_SOURCE_ID", 该值为常量，表示消息平台需要从业务数据中取出名为“userSourceId”的属性，作为真实的互联网AppId。

::: tip 提示
* 新增应用时必须填写互联网AppId和应用名，并指定应用类型。
* 更新应用时，<font color=red>不允许更新互联网AppId和应用类型</font>。
:::

### 2.1 Android App
<img :src="$withBase('/app.png')" alt="img">


### 2.2 iOS App
<img :src="$withBase('/app.png')" alt="img">

### 2.3 微信公众号
<img :src="$withBase('/app.png')" alt="img">

### 2.4 微信小程序
<img :src="$withBase('/app.png')" alt="img">

### 2.5 支付宝小程序
<img :src="$withBase('/app.png')" alt="img">

## 3 业务场景
<img :src="$withBase('/app.png')" alt="img">

### 3.1 新增业务场景
点击业务类型标题，进入业务类型编辑页面。
<img :src="$withBase('/app.png')" alt="img">

### 3.2 编辑业务场景
参考新增业务场景页面。

### 3.3 删除业务场景
业务场景删除，对应的消息定义与应用内消息定义均同步删除。

### 3.4 新增消息定义
点击“新增消息定义” > 选择消息类型  >   进入消息定义新增页面。

>当前消息平台支持以下类型消息：

* Android小米推送，消息类型编码：<font color=red>ANDROID_XIAOMI_PUSH</font>。向小米品牌的Android客户端推送消息时，需要使用该消息类型。
* iOS小米推送，消息类型编码：<font color=red>IOS_XIAOMI_PUSH</font>。向苹果iPhone或iPad等设备推送消息时，需要使用该消息类型。
* 华为推送，消息类型编码：<font color=red>HUAWEI_PUSH</font>。向华为品牌设备推送消息时，需要使用该消息类型。
* 微信公众号模板消息，消息类型编码：<font color=red>WECHAT</font>。该类型消息只需指定用户id，而不用指定公众号应用id。
* 微信小程序模板消息，消息类型编码：<font color=red>WX_MINI</font> 。该类型消息需要指定公众号应用id，且该公众号需要与小程序关联。最终消息会发送到指定公众号首页。
* 微信小程序订阅消息，消息类型编码：<font color=red>WX_SUBSCRIBE</font>。该类型消息会发送至微信首页。
* 支付宝小程序订阅消息，消息类型编码：<font color=red>ZFB_SUBSCRIBE</font>。该类型消息会发送至支付宝首页，某些消息会通过支付宝App推送发送至用户手机状态栏。
* WebSocket消息，消息类型编码：<font color=red>WEB_SOCKET</font>。该类型消息主要服务于公众号，PC网页或移动H5应用。
* 业务定制消息，消息类型编码：<font color=red>CUSTOM_XXX</font>。编码以"CUSTOM_"开始，长度在10~32之间。 当需要发送定制消息时可以使用该消息类型。

::: warning 
除业务定制消息外，其它类型均为系统内置，不允许修改
:::

#### 3.4.1 Android小米推送
<img :src="$withBase('/app.png')" alt="img">

点击属性编辑图标，进行属性编辑页面。如编辑通知栏内容

<img :src="$withBase('/app.png')" alt="img">

#### 3.4.2 iOS小米推送
因苹果公司对iOS设备具有极强的控制能力，iOS平台的推送只需要接入任一家厂商即可。
<img :src="$withBase('/app.png')" alt="img">

在消息平台中，iOS小米推送作为iOS平台惟一的推送通道。

#### 3.4.3 华为推送
<img :src="$withBase('/app.png')" alt="img">

#### 3.4.4 微信公众号模板消息
<img :src="$withBase('/app.png')" alt="img">

::: tip 注意
公众号消息跳转小程序，需要将公众号与小程序进行绑定。
:::

#### 3.4.5 微信小程序模板消息
同 微信公众号模板消息

#### 3.4.6 微信小程序订阅消息
<img :src="$withBase('/app.png')" alt="img">

#### 3.4.7 支付宝小程序订阅消息
同微信小程序订阅消息

#### 3.4.8 WebSocket消息
<img :src="$withBase('/app.png')" alt="img">

#### 3.4.9 业务定制消息
业务定制消息没有固定的内容格式，需要由业务系统根据实际需求提供。

消息平台在完成数据处理，消息解释，路由等工作后，将调用指定的业务系统完成消息发送。
<img :src="$withBase('/app.png')" alt="img">

### 3.5 编辑消息定义
点击某类型消息定义，进入消息定义编辑页面。

消息定义页面与编辑页面大致相同，不再展开说明。

### 3.6 启用/禁用消息定义
消息定义为启动状态，当业务信息提交时，会触发该定类型消息发送发送。反之则不会触发该类型消息发送。

### 3.7 新增应用内消息
在应用的消息中心查询到的消息称为应用内消息。应用内消息外观及数据格式由管理员通过消息平台录入。

<img :src="$withBase('/app.png')" alt="img">

::: tip 注意
* 配置完成并启用后，才能在消息中心查看对应的应用内消息。且在此之前的消息无查询到。
* 这里需要注意的是，为了兼容不同平台点击跳转事件，可以根据实际情况配置点击跳转H5页面，小程序页面（支付宝或微信小程序），及App原生页面及参数。
:::

### 3.8 编辑应用内消息
与新增应用内消息页面大致相同，不再展开说明。

### 3.9 启用/禁用应用内消息
应用内消息禁用后，新产生的业务信息将无法在消息中心查看。之前已经存在的消息不受影响。

### 3.10 测试
<img :src="$withBase('/app.png')" alt="img">

## 4 数据统计
<img :src="$withBase('/app.png')" alt="img">

## 5 记录查询
<img :src="$withBase('/app.png')" alt="img">

点击“查看详情”，可进入提交详情页面
<img :src="$withBase('/app.png')" alt="img">

## 6 接收者管理
<img :src="$withBase('/app.png')" alt="img">

## 7 消息模板
<img :src="$withBase('/app.png')" alt="img">

::: tip 
* 模板管理提供了模板便捷录入，更新和实时预览功能。
* 同一个模板被不同的应用引用后，会生成不同的模板id，所以在模板维护完成后，需要在应用管理中进行关联（模板编码与模板id关联）。
* 最终模板消息（公众号模板消息，微信小程序订阅消息，支付宝小程序订阅消息）都需要使用模板id来进行发送。
:::

### 7.1 微信模板消息
<img :src="$withBase('/app.png')" alt="img">

### 7.2 微信订阅消息
<img :src="$withBase('/app.png')" alt="img">

### 7.3 支付宝订阅消息
<img :src="$withBase('/app.png')" alt="img">

## 8 配置导出/导入
### 8.1 导出
<img :src="$withBase('/app.png')" alt="img">

### 8.2 导入
<img :src="$withBase('/app.png')" alt="img">