###UIWebView 混合编程
####模板引擎
[**MGTemplateEngine**](https://github.com/mattgemmell/MGTemplateEngine)

[**GRMustache**](git@github.com:groue/GRMustache.git)
####OC与JS互调
[**WebViewJavascriptBridge**](git@github.com:marcuswestin/WebViewJavascriptBridge.git)

###应用内支付
[in-App-Purchase](https://developer.apple.com/library/prerelease/content/qa/qa1329/_index.html)

###开发技巧
####UILable Frame origin不为整数，显示会模糊
####收起键盘
* VC重载touchBegin方法,执行[self.view endEditing:YES],单击任何VC地方都收起键盘
* 直接执行    [[UIApplication sharedApplication] sendAction:@selector(resignFirstResponder) to:nil from:nil forEvent:nil];当获取VC比较困难时用
* [[[UIApplication sharedApplication] keyWindow] endEditing:YES];

####NSJSONSerialization比NSKeyedArchiver好，效率、体积上更优
[测试](https://github.com/randomsequence/NSSerialisationTests)
####系统内控制语言
* UIWebView长按弹出上下文
* UIImagePickerController系统照相机界面
* UITableViewCell编辑状态下删除显示

**他们的语言显示不与手机设置一致，而与应用内语言设置有关**

![](./系统内控制语言.png)

####巧用截屏
iOS7之后使用`[[UIView new] snapshotViewAfterScreenUpdates:]`,iOS7之前使用

```
+(UIImage *)captureImageFromView:(UIView *)view{
    CGRect screenRect = [view bounds];
    UIGraphicsBeginImageContext(screenRect.size);
    CGContextRef ctx = UIGraphicsGetCurrentContext();
    [view.layer renderInContext:ctx];
    UIImage *image = UIGraphicsGetImageFromCurrentImageContext();
    UIGraphicsEndImageContext();
    return image;
}
```
**用截屏实现侧滑返回效果，带半透明效果，如QQ,WECHAT.push时把截屏传过去给VC，充当其背景内容，当手指右滑时，把VIEW右移，截屏相应右移，并调整透明度，操作完成pop到上一个VC**

####忽略编译警告
编译文件标志写上`-w`或`-Wno-unused-variable`
####XCODE技巧
* `cmd+shift+O`  或  `ctrl + 6`
* Behavious 设置
* 查找功能 `Insert Pattern`
* 清除编译缓存 DerivedData
* 下载XCODE `https://developer.apple.com/downloads/index.action`

####Daily Build
[lexrusg开源](https://github.com/lexrus/ios-makefile)
####删除未使用的图片
brew install ack
####图像处理库
brew install imagemagick

###工具集
* [第三方库依赖cocoapods]()
* [网络封包分析工具Charles]()
* [Reveal界面调试工具]()
* [统计工具Flurry]()
* [崩溃日志记录工具Crashlytics]()
* [App Store统计工具App Annie]()

###插件
####插件管理Alcatraz
* KSImageNamed:自动弹资源上下文
* XVim:xcode 下的vim插件
* FuzzyAutocompletePlugin:模糊自动补全代码
* XToDo:查找项目中带TODO,FIXME,???,!!!的注释
* BBUDebuggerTuckAway:编辑代码时自动隐藏DEBUG窗口
* SCXcodeSwitchExpander:自动填充switch语句
* deriveddata-exterminator:自动清除缓存目录
* VVDocumenter:自动生成代码注释，并可系统查看
* ClangFormat:自动缩进，调整代码风格
* ColorSense:UIColor预览颜色
* XcodeBoost:多种辅助功能，1把文件方法暴露在头文件中2源文件输入正则查找3复制粘贴不启动系统缩进功能

####其他工具
* 系统自带数码测色计,类似xScope
* ImageOptim:图像压缩
* markman:标注工具
* Dash:API文档查询，代码块管理工具
* 蒲公英:内测分发
* nomad:命令行操作苹果开发中心`gem install nomad-cli`
* xctool:命令行iOS编译和测试工具  `brew install xctool`
* appledoc:抽取文档生成与系统一样的说明文档工具 `brew install appledoc`



