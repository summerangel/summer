---
layout: '[layout]'
title: The project of react-native come to an end
date: 2018-07-11 21:09:11
tags: react-native
---

#### Say goodbye to react-native project temporarily

  So busy these days that I don’t have time to update my blog and learning,sad.
  After struggling in the react-native for several months, solved the environment for developing and have an knowledge of the grammar of react-native,feel so released, and not that afraid of react-native.

#### Some issue met record

   1、Using picture as background image to implement the shadow in order to cross platform which takes effect in both ios and android.

   The shadow realised by css in react-native is not like the way in web css.
   In normal web css you can realise it by the attribute like the writing of: box-shadow: 10px 10px 5px #000;(just an example);
   But in react-native,you should write it like this:

   1) shadowColor color string (shadow color)
   2) shadowOffset {width: number,height: number} (shadow offset)
   3) shadowOpacity number (shadow opacity)
   4) shadowRadius number (shadow radius)

   ```
   <View style={{
      width: 100,
      height: 100,
      backgroundColor: 'red',
      shadowColor: 'green',
      shadowRadius: 10,
      shadowOpacity: 0.5,
      shadowOffset: {width: 20,height: 20}
   }}>
   </View>
   ```
   Due to this is only taking effect in ios,so here I use the shadow picture as the background Image to implement the effect.

   2、Date format can not be transferred as expected

   Actually I met this issue years ago,which only the format of 2018/7/11 can be correctly transferred in ios,we should use slash to split the number.
   If not slash, use comma or dot or transverse line will get null.

   3、Error watching file for changes: EMFILE

   Fix: just install watchman: brew install watchman

   4、npm ERR! Failed at the uglifyjs-webpack-plugin@0.4.6 postinstall script.

   Met this when deploy the project into the server, execute the command: npm install
   Fix: you can use yarn or update the npm.(Experience said: when met some unexplainable issue excuting npm install, you can upgrade or down version of npm.

   5、iOS: UI will be blocked when show Alert while closing Modal

   Fix: [Reffer to this link](https://github.com/facebook/react-native/issues/10471)

#### Bundle ios

  1、Run ios: react-native run-ios;
  2、Bundle ios: react-native bundle --entry-file index.js --platform ios --dev true --bundle-out ./ios/bundle/index.jsbundle --assets-dest ./ios/bundle

#### Conclusion

  The project is just finished like this, feel a little lost, thought the process to learn react-native is hard but still happy and satisfied.














