# TravelManagementCompanies

# TMC项目iOS端 

 - 项目为OC语言编写，其中已经桥接了swift头文件，可用swift语言继续编写;
 - 使用cocoapods管理第三方库文件；
 - 项目运行在xcode上，请运行后缀为  .xworkspace  的文件

_ _ _

## iOS 打包流程

1. 在ionic 项目目录下运行 命令：
	Ionic cordova build ios 
	生成iOS原生可执行文件
2. 创建APP Bundle Identifier
3. 申请IOS 发布证书
4. 申请IOS发布描述证书
5. 上传iOS证书编译打包IPA
6. 在iTunes Connect创建APP
7. 在Application Loader中上传IPA到iTunes Connect


### 请安装Xcode 9.0 以上版本

### 一、创建唯一标示符BundleID   (App IDs)

APP IDs在后面创建发布文件，创建APP时都要用到。（appid非常重要，整个上架流程就是用appid关联在一起）
如果之前iOS真机调试时创建过了，就不用重新创建了，还是用那个appid。
首先打开[开发者中心](https://developer.apple.com/account), 进入证书页面

1.1点击证书、ID及配件文件，进入设置；
![](https://upload-images.jianshu.io/upload_images/4874746-84c935b6cba9b66b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)

1.2选择App IDs –>点击+创建一个新的App ID
![](https://upload-images.jianshu.io/upload_images/4874746-90fa268939dddd4a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)

其中有两项需要你自己填：

第一项Name，用来描述你的App ID，这个随便填，没有什么限制，最好是项目名称，这样方便自己辨识（不允许中文）

第二项Bundle ID (App ID Suffix)，这是你App ID的后缀，需要仔细填写。用来标示我们的 app，使它有一个固定的身份，和你的程序直接相关。填写  Explicit App ID 的格式为：com.company.appName（要有两个点.）照着格式写，写个方便记的.

像这串com.yesgame.tianbiao就是appid了，后面申请ios证书、打包ipa和在itunesconnect创建APP就是用这个格式的appid。

整个app上架流程就是靠这个appid关联在一起。

第三项配置服务权限，默认会选择2项，不能修改，其它常用的苹果支付，APP推送通知，根据自己需要的服务选择上，然后点击Continue确认，下一步。

选择苹果支付和推送通知，还需要创建对应的iOS苹果支付证书和iOS推送证书。
![](https://upload-images.jianshu.io/upload_images/4874746-6de6ac535b5a5760.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)

一般没什么要求默认就好。
![](https://upload-images.jianshu.io/upload_images/4874746-8b4889fdcbbee2fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/650)
检查下没有错的话直接点击Register后点击Done完成App ID的创建。

<!-- ### 二、申请发布证书

iOS各类证书申请教程、各种证书用法不同。

[iOS开发证书申请](https://link.jianshu.com/?t=http%3A%2F%2Fwww.applicationloader.net%2Fblog%2Fzh%2F164.html)（xcode开发手机测试）

[iOS发布证书申请](http://www.applicationloader.net/blog/zh/100.html)（发布上架App Store）

[iOS推送证书申请](https://link.jianshu.com/?t=http%3A%2F%2Fwww.applicationloader.net%2Fblog%2Fzh%2F397.html)（APP推送通知）

[iOS真机调试证书申请](https://link.jianshu.com/?t=http%3A%2F%2Fwww.applicationloader.net%2Fblog%2Fzh%2F216.html)（安装到非越狱手机测试）

[iOS企业证书申请](https://link.jianshu.com/?t=http%3A%2F%2Fwww.applicationloader.net%2Fblog%2Fzh%2F694.html)（免上架App Store安装手机使用）

这里是上架App Store所以申请iOS发布证书 -->

### 二、添加证书

1. 进入苹果开发者中心选择Provisioning Profiles描述文件
2. 点击添加按钮，如图：
![](https://upload-images.jianshu.io/upload_images/2069062-bc7ca1c109b863f4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

3. 选择证书

* 开发证书（Development）：最多1个（20170425日只能生成一个了）
* 发布证书（Production）：最多3个（网传）
![](https://upload-images.jianshu.io/upload_images/2069062-795c1f3d5f9e4beb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

4. 准备创建CSR文件（这里以Production 的 App Store And AD Hoc为例）
![](https://upload-images.jianshu.io/upload_images/2069062-6b31133f3098f6cb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

5. 创建CSR文件01（打开钥匙串->证书助理->从证书颁发机构请求证书）
![](https://upload-images.jianshu.io/upload_images/2069062-80db551d6997d5e6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

6.创建CSR文件02（填写电子邮件地址，常用名称，这两项都可以随便填，注意要把CSR文件存储到磁盘）
![](https://upload-images.jianshu.io/upload_images/2069062-0f06fd5ad2c2a54d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

7. 创建CSR文件（为CSR文件取名，建议最好取一个和你项目名称相关的名字）
![](https://upload-images.jianshu.io/upload_images/2069062-87f15b4267e44474.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

8. 选择刚刚创建的CSR文件
![](https://upload-images.jianshu.io/upload_images/2069062-bca2c806ce34f840.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

9.创建证书完毕，下载证书
![](https://upload-images.jianshu.io/upload_images/2069062-fe782d541043446e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

注：Extension：CSR是Cerificate Signing Request的英文缩写，即证书请求文件，也就是证书申请者在申请数字证书时由CSP(加密服务提供者)在生成私钥的同时也生成证书请求文件，证书申请者只要把CSR文件提交给证书颁发机构后，证书颁发机构使用其根证书私钥签名就生成了证书公钥文件，也就是颁发给用户的证书。

### 三、添加设备（如果只是发布，此步骤可跳过）
1. 添加测试设备

![](https://upload-images.jianshu.io/upload_images/2069062-fdcd760624d80e3d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

2. 获取设备的UDID（iTunes或者Xcode获取）
![](https://upload-images.jianshu.io/upload_images/2069062-1ed941b2dcb69a23.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

![](https://upload-images.jianshu.io/upload_images/2069062-a34863027a8f2f6e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

3.注册设备

![](https://upload-images.jianshu.io/upload_images/2069062-2cae046465b255ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

注:这里的设备在开发者付费后1年内最多只能添加100台，如果没有在这里配置Device的UDID，Xcode在登录过开发者账号的情况下, 也可以自动修复

### 四、配置包含以上三者信息的描述文件
1. 添加描述文件

![](https://upload-images.jianshu.io/upload_images/2069062-15d4ad0edbb797b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

3. 选择对应的AppID，如果之前AppID是按照项目名取的，这里就很好找。所以说取名一定要有套路，一定要规范！
![](https://upload-images.jianshu.io/upload_images/2069062-3469bab17fa76344.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

4. 选择对应的证书（之前是可以默认全部勾选的，但是现在不可以了，所以只能选择刚才创建的证书，看名字不好辨别，只能根据证书到期日期判断，比如今天是2017年3月19日，所以推断出，2018年3月18日的那个证书是刚刚创建的）
![](https://upload-images.jianshu.io/upload_images/2069062-3c0cbd0346570416.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

5. 如果配置开发证书，这里还要多一步，选择设备，直接全部选择就好了
6. 给描述文件取名（一定要规范！一定要规范！！一定要规范！！！）
![](https://upload-images.jianshu.io/upload_images/2069062-1730ec63e1a809c3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

7. 下载描述文件

![](https://upload-images.jianshu.io/upload_images/2069062-4b09789269790aaa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

### 五、配置完成, 安装证书和描述文件
    直接双击即可安装（建议先安装证书, 再安装描述文件）

### 六、xcode配置iOS证书和打包环境,打包、生成IPA
1. 双击.mobileprovision描述文件也是就是上面你配置好并且下载到本地的描述文件，闪一下就自动导入到xcode，不报错表示可以了。
![](http://www.applicationloader.net/blog/wp-content/uploads/2017/02/7.1-768x624.png)

2. 如下图所示，打开工程文件后，请先填写Bundle Identifier：此ID为你在开发者中心注册的app id，
然后选择对应的描述文件，该位置如图中箭头所示

![](https://github.com/cntehang/TravelManagementCompanies/blob/master/Pasted%20Graphic.tiff)

3. 选择xcode菜单栏如果图所示
![](http://www.applicationloader.net/blog/wp-content/uploads/2017/02/11.png)

4. 把Archived修改为Release
![](http://www.applicationloader.net/blog/wp-content/uploads/2017/02/26.png)

5. 点击选择设备，选择为打包设备
![](http://www.applicationloader.net/blog/wp-content/uploads/2017/02/15-768x392.png)

6. 点击Archive，开始打包。
![](http://www.applicationloader.net/blog/wp-content/uploads/2017/02/16.png)

7. 打包进度条走完后，会弹出以下界面，点击Expcrt
![](http://www.applicationloader.net/blog/wp-content/uploads/2017/02/17.png)

8. 这里是个人开发账户发布到App Store，所以选择第一项，点击Next。测试调试的选第二项。
![](http://www.applicationloader.net/blog/wp-content/uploads/2017/02/18.png)

9. 选择你的开发者账号，还没登录会提示你登录，点击Choose，会检查你的证书是否正确。
![](http://www.applicationloader.net/blog/wp-content/uploads/2017/02/19.png)

10. iOS证书检测通过就到了这一步、点击Export，就会导出 一个文件夹，里面就是IPA文件，大功告成了。
![](http://www.applicationloader.net/blog/wp-content/uploads/2017/02/22.png)

![](http://www.applicationloader.net/blog/wp-content/uploads/2017/02/21.png)




### 七、发布App
1. 登录[iTunes Connect](https://link.jianshu.com/?t=https://itunesconnect.apple.com)

2. 新建App
![](https://upload-images.jianshu.io/upload_images/2069062-3729e15ed26f7f72.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

3.填写相应的信息

![](https://upload-images.jianshu.io/upload_images/2069062-501d036bb119cd56.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

4. 填写相应的信息（如果平面设计师没有给提供，可以自己用模拟器截图（快捷键Commond + S），最新规定只传5.5寸的就可以了）
![](https://upload-images.jianshu.io/upload_images/2069062-76244e606c8b4c5c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

5. 填写相关信息
![](https://upload-images.jianshu.io/upload_images/2069062-db162f119df50a7a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

6. 对app编辑分级
![](https://upload-images.jianshu.io/upload_images/2069062-8fff7003c22248e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

7. 填写app综合信息
![](https://upload-images.jianshu.io/upload_images/2069062-7aff27ba9d3d0629.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

8. 填写App审核信息,演示账户及密码
![](https://upload-images.jianshu.io/upload_images/2069062-71f2d33f7c4ac05f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

9. 版本发布选择
![](https://upload-images.jianshu.io/upload_images/2069062-2af284471785fff8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

10. 保存填写完的信息
![](https://upload-images.jianshu.io/upload_images/2069062-5ddf3aca488b7661.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

11. 准备添加app版本
![](https://upload-images.jianshu.io/upload_images/2069062-7a594d11e8085bc2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

12. 构建版本
![](https://upload-images.jianshu.io/upload_images/2069062-474864340f497d9c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

13. 提交以供审核
![](https://upload-images.jianshu.io/upload_images/2069062-f6f5e81759708f7d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

14. 内容版权和广告标识符
![](https://upload-images.jianshu.io/upload_images/2069062-85e48121d6190090.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

15. 最后一步：提交
![](https://upload-images.jianshu.io/upload_images/2069062-ddd7e275943f531e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

