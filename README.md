# cordovaNotes
cordova/ionic相关笔记

##编译工程   
ionic build

##ionic替换图标／启动页   
替换 resources 目录下的 icon.png （192*192）／splash.png    
ionic resources --icon   
ionic resources --splash   

##跑在真机上    
安卓：ionic run android     
ios: 编译后 xcode 直接真机      

##android 打出未签名的包    
cordova build --release android

如出现问题在 platforms/android/build.gradle 文件的android {} 节点中增加

lintOptions{    
    abortOnError false    
    checkReleaseBuilds false     
}

##指定 android 最低版本    
在 config.xml 中加入
        <preference name="android-minSdkVersion" value="19" />
其中 value 为 api level，安卓版本和API关系：     
https://en.wikipedia.org/wiki/Android_version_history       
参考：    
http://stackoverflow.com/questions/27135185/how-can-i-specify-the-minimum-sdk-in-phonegap-it-is-ignoring-android-minsdkvers

##为android添加crosswalk插件    
添加：cordova plugin add cordova-plugin-crosswalk-webview    
移除：cordova plugin remove cordova-plugin-crosswalk-webview

crosswalk插件作用：使用 chrome webview 做 app 容器，android 4.4以下明显提高流畅性，且解决css3高级属性兼容性问题    
使用 crosswalk 打包会生成两个apk文件 armv7 和 x86 （使用armv7)     
带来影响：安装包大20M左右

##ios build 相关问题     
引入第三方库，真机调试发现 build 报错 bitcode      
‘/Users/**/Framework/SDKs/PolymerPay/Library/mobStat/lib**SDK.a(**ForSDK.o)’does not contain bitcode.     
在项目配置中搜索 bitcode，将 yes 改为 true      
参考：http://www.jianshu.com/p/3e1b4e2d06c6

ios9 无法发送 http 请求     
在Info.plist中添加NSAppTransportSecurity类型Dictionary        
在NSAppTransportSecurity下添加NSAllowsArbitraryLoads类型Boolean,值设为YES      
参考：http://segmentfault.com/a/1190000002933776



