---
layout: '[layout]'
title: Holes in exploring react native
date: 2018-05-28 22:58:57
tags: react-native
---

#### 一、Hole one

  When installing the react-native environment, confront the following:

{% asset_img hole_one.jpg caused by file missing %}

 It took me almost one day to find this problem out,for I was first day to come this group to work on this react-native project,though I found another way to
 fix this,I was curious to know what mistake cause this. Ok, focus came,it was caused by some missing files, which may be the window's fault(another colleague passed it to the git repository using window system computer,then the window didn't treat that file as a file, because it was treated as a reference addresss in ios,according to my ios
 colleague), red rectangle is the missing file.

{% asset_img hole_reason.jpg caused by file missing %}

#### 二、Debug in Browser (Mac ios)

 1、 Press command + D in simulator, then the debug menu will show;
 2、 Menu One: Reload, equal to the quick command: command + R;
 3、 Menu Two: Debug JS Remotely, will open it in browser( http://localhost:8081/debugger-ui ) for you,let you debug like web project;

   Reference to [this article](http://www.hangge.com/blog/cache/detail_1480.html)

#### 三、Day two

  This was a fucking day,all the whole day was fixing the stupid bug caused by others.

  1、 Bug one: Infinite callback caused by realm when the version above 2.0.6, so to fix this,
  you guys need to install the version 2.0.6,may be the author will fix this later.

   Reference to [this issue](https://github.com/realm/realm-js/issues/1538)

  2、 Bug two: post can not be transferred to the backend,although there exists
  [same issues](https://github.com/axios/axios/issues/1321), we here are caused by
  ourselves.

  3、 Bug three: may be you guys will meet this, fixing: just install the library they
  needed.

 {% asset_img bug_three.jpg problem may be met %}

  4、 Tools: React Native Debugger, this is a good debugger tool to modify css and debugger js,
  I think it's better than Chrome,of course,if you like it too,please support the
  author,give [the repo](https://github.com/jhen0409/react-native-debugger) a star: https://github.com/jhen0409/react-native-debugger

#### 四、Support http in ios

   By default iOS isn’t supporting HTTP requests, only HTTPS requests are allowed.Make ios support http please refer to
   [this article](http://www.competa.com/blog/react-native-ios-http-network-request-failed/),following is an example screenshot
   to solve this:
{% asset_img solve_img.jpg example screenshot%}

#### 五、library not found for -lQBImagePickerController

  This was caused by opening the wrong file here which should open workspace file, not project file. see [here](https://github.com/ivpusic/react-native-image-crop-picker/issues/27)
  （Actually this don't solve my problem, because another problem came out, xcode is so annoying,want to say bad words）

#### 六、The holes met in exploring to run project in my real phone

   1、First give an [article](https://www.jianshu.com/p/f31116a76ea9) about how to config xcode to run in your real phone

   2、Your development team "xxx" does not support the Push Notifications capability
    Solve method:
    In your edit software to open xxx.entitlements like, find and delete "<key>aps-environment</key>", then save this file.
  Refer to [this article](https://www.jianshu.com/p/ae0afe79c6bd)

   3、Xcode not supported for iOS 11.4 by Xcode 9.2 needed 9.4，explain this by a screenshot:

{% asset_img unpair.jpg not supported screenshot %}

  Find solving method in [this article](https://stackoverflow.com/questions/49720178/xcode-not-supported-for-ios-11-3-by-xcode-9-2-needed-9-3)
  You can download [iOS 11.4 (15F79)](http://www.mediafire.com/file/7m25vq8l35eplws/11.4+%2815F79%29.zip) and put it in the directory of 'Xcode.app//Contents/Developer/Platforms/iPhoneOS.platform/DeviceSupport'(you can open this by right click the icon of xcode in application,select the second one Show package Content),[may be this one give you more detail](https://www.jianshu.com/p/7f662bfce732).
  Or update xcode to [9.4](https://itunes.apple.com/us/app/xcode/id497799835?ls=1&mt=12)

   4、The entitlements specified in your application’s Code Signing Entitlements file are invalid, not permitted, or do not match those specified in your provisioning profile. (0xE8008016).

   Takes hours to fix this, thanks this guy very much,you are hero: [finally fixed this annoying issue](https://stackoverflow.com/questions/40985359/entitlements-dont-match-provisioning-profile-0xe8008016)
    records here:
       1) Select your project in the Project navigator;
       2) Select the "General" tab;
       3) To the left of the "General" tab, select your target to the left; (this should show a dropdown with a list of targets);
       4) Below your current target you should see an item {your project}Tests; select that;
       5) Check the signing properties in the general tab and make sure they are valid.

   5、Finally,the environment to run the project in my real phone is completely finished,I feel so happy though the process to config the xcode as a new fellow is really fucking and freaking out.

#### 七、Follow-up

  After configed the xcode to run project in my real phone, it is not the way I expected to, so I back to use the command way to debugger my project, still spent the whole morning to fix it.

  records: There exists bug in using absolute css attribute in Android.

#### 八、Bad thing for me

  May be clean unuseful files for more memory, I have cleaned the screenshots of this article, the update for my website need to be planned.

#### 九、Exploring react-native-snap-carousel

I want to realise certain css style,but simply look the api in react-native-snap-carousel isn't met my requirement,so I download the source code to explore it in the examples the author give,but after installed all the dependencies,it just can't run it,finally find [the way to fix this](https://github.com/archriss/react-native-snap-carousel/issues/93)
Just use yarn instead of npm fix this, happily exploring.

#### 十、Another skill get

 It is necessary to have effective tools to do good work. Every time it's so exciting to find a better way to optimize existing work environment.Till now, the environment to develop react-native is almost fully done.As everyone knows,react-native doesn't support the way to see request.Yesterday this was denunciated by back-end colleague,which effects development severely, I was frustrated by what he said, so googled,and finally found a way to fix this.
 Ok,focus come,(hehe....so many junk words),it is to use Charles to catch the request fetch by pages.[Here is an article teach you how to config it](https://www.jianshu.com/p/3bfae9ede35e)
 I installed and configed Charles before(I used to develop in hybrid),so here I just to install the certificate at Charles(select Help --> SSL Proxy --> Install ... in IOS simulator) and then trust it in my IOS simulator(go to Setting --> General --> About --> Certificate Trust Settings, and then trust it)
 Finally, I can develop with all the configs happily,and It saves a lot of time.The following is now my work space looks like:
{% asset_img work_environment.jpeg caused by file missing %}

#### 十一、Hole in css

 It is not like web css to make an image circle just use border-radius the image's width or height or 50%, you should give the attribute borderRadius half of the width or height of the image;