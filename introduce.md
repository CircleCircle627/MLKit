# 机器学习服务（ML Kit）

## 业务简介
&emsp;华为机器学习服务（ML Kit） 提供机器学习套件，为开发者应用机器学习能力开发各类应用提供优质体验。得益于华为长期技术积累，ML Kit为开发者提供简单易用、服务多样、技术领先的机器学习能力，助力开发者更快更好的开发各类AI应用。

## 服务介绍
### 文本类
- **文本识别**

&emsp;文本识别服务可以识别收据、名片、文档照片等含文字的图片，将其中的文本信息提取出来。该服务广泛应用于办公、教育、出行等各类app。例如，您可以在翻译应用中，使用该服务提取照片文本，提交翻译，轻松实现拍照翻译功能，提升用户出行体验。

&emsp;该服务能同时支持设备端和云端，但是其能识别的文字种类有区别。端侧服务支持识别中文（简体）、日文、韩文、拉丁字符（支持的拉丁字符参见文字识别客户端支持的拉丁字符）。云侧接口支持识别中文（简体）、英文、西班牙文、葡萄牙文、意大利文、德文、法文、俄文、日文、韩文、波兰文、芬兰文、挪威文、瑞典文、丹麦文、土耳其文、泰文、阿拉伯文、印地文等文字。

- **文档识别**

&emsp;文档识别服务可以从含有文档的图片中，比如文章、合同等，能识别出带段落格式的文本信息。该服务可以从文档材料中提取对应的内容，快速实现从纸质文件到电子文件的转化，大幅提升信息的录入效率，降低人力成本。

- **身份证识别**

&emsp;身份证识别服务提供对中国大陆第二代居民身份证的识别，从带有身份证信息的图像或视频流中，识别出带格式的文本信息。该服务可以对身份证信息做结构化识别和录入，在保险、金融、电商等需要实名认证的行业中广泛应用，不仅可以降低用户身份证信息录入错误的风险，还能以便捷的操作提升用户体验。

- **银行卡识别**

&emsp;银行卡识别服务可以快速识别卡号等关键信息，覆盖全球常见卡证类型，包括银联、美国运通、万事达（Mastercard）、 Visa 、 JCB等。该服务广泛应用于金融、支付等绑卡场景中，可以快速提取对应信息，实现轻松录入。

- **通用卡证识别**

&emsp;通用卡证识别服务基于文字识别技术，提供通用的开发框架。针对港澳通行证、香港身份证、回乡证等任意固定版式的卡证，支持开发者自定义后处理逻辑获取所需信息。当前版本提供视频流、拍照和本地图片三种接口，并支持定制识别界面，满足开发者多样化的使用场景。例如，用户在预定境外酒店、机票等场景中，可以快速自动识别相关证件，完成高效录入。

### 语言类
- **文本翻译**

&emsp;文本翻译服务可以检测源语言的语种类别，并在多语种间相互转化，当前支持中文（简体）、英文、法文、阿拉伯文、泰文、西班牙文、土耳其文、葡萄牙文、日文，德文、意大利文和俄文12种语言文字间的互译。例如，可以在教育学习类应用中加入该功能，轻松实现将陌生语言翻译成熟悉的语言。

- **语种检测**

&emsp;语种检测服务支持对语种文本的检测，目前能实现49种语言检测。支持语言的详细信息请参见语种检测支持的语言列表。例如，用户可以轻松实现翻译语种检测、网页语种检测，混合语种场景中语种检测等。

### 图像类
- **图片分类**

&emsp;通过对图片中的实体对象添加标注信息，如：人、物、环境、活动、艺术形式等信息，帮助定义图片题材和适用场景等。标注信息列表参见图片分类类别清单。例如，您可以在图片管理类应用中，完成不同类别图片的快速筛选。

- **对象检测和跟踪**

&emsp;您可以对图片中多个对象进行位置信息的跟踪与检测，基于此服务您可以实时定位和跟踪对象、对象分类等。在图片审核、拍照识图等场景中有广泛应用。例如，您可以实时获取对象的位置状态，进行相关分析；还可以进行图片筛选应用的开发，通过类别划分，过滤不感兴趣的某几类对象。

- **地标识别**

&emsp;您会获得输入图片的地标名称、经纬度信息，基于获得的信息，您可以为用户创造更加个性化应用体验。例如，旅游类应用中可以识别图片中地标建筑，告知用户地标位置并推送旅游信息。

- **图像分割**

&emsp;图像分割服务可以将图片中不同元素的内容分割出来。例如，在照片美颜或图片编辑的应用中，通过分割人像和背景，随意替换背景，提升应用的可玩性。

- **拍照购物**

&emsp;用户通过拍摄或扫描商品图片，在线检索相似商品信息，返回商品ID和图片信息。例如，在购物类应用中，可以使用此服务，快速查找明星同款、进口商品、商品比较等。

### 人脸人体类
- **人脸检测**

&emsp;检测人脸轮廓，识别人脸面部特征，包含表情、年龄、性别、穿戴等信息。例如，您可以在视频聊天中给头像添加动态美颜、动态素材，提升视频聊天体验。

## 设备端和云端API
&emsp;机器学习服务提供了设备端和云端的API接口，设备端API的处理速度更快，在无网络连接也可正常工作。云端API可以处理更加复杂的场景，准确性更高。ML Kit 设备端API使用不限次数，云端API服务按照单个产品的服务场景计算次数，详情页面请参考[服务开通](https://developer.huawei.com/consumer/cn/doc/development/HMS-Guides/ml-enable-service)。

## 隐私声明
&emsp;在基于HMS SDK开发时，您需要遵守《[华为开发者服务协议](https://developer.huawei.com/consumer/cn/doc/start/20201)》、《[华为APIs使用协议](https://developer.huawei.com/consumer/cn/doc/distribution/app/20209)》、《[AppGallery Connect数据处理附录](https://developer.huawei.com/consumer/cn/doc/distribution/app/20215)》和《[华为机器学习服务使用协议](https://developer.huawei.com/consumer/cn/doc/jiqixuexi)》。机器学习服务不会保存任何个人数据和图像数据。

## 华为机器学习服务支持的地区
&emsp;请参考[华为机器学习服务支持的地区](https://developer.huawei.com/consumer/cn/doc/development/HMS-Guides/ml-region-4)。
