AndroidMultiChannelBuildTool
============================

安卓多渠道打包工具。  
实现思路讲解： [Android批量打包提速 - GavinCT](http://www.cnblogs.com/ct2011/p/4152323.html)  

使用本工具，Android程序员仅需将ChannelUtil.java放入到工程里使用，以后打包的事情就不用自己动手了。  
安装个Python环境，运行一下MultiChannelBuildTool.py，谁都可以打包了！
# 写在最前面
本工具不支持v2签名，如有需要，请使用[Meituan-Dianping/walle](https://github.com/Meituan-Dianping/walle)
# 具体使用步骤
将想要批量打包的apk文件拷贝到PythonTool目录下（与py同级），运行py脚本即可打包完成。（生成的渠道apk包在output_** 目录下）
# 目录介绍及使用注意
## PythonTool
Python2 与 Python3 都能正常使用 

- info目录下的channel用来存放渠道，多个渠道之间用换行隔开。  
  注意：  
  fork后通过Github clone，这个channel文件在Windows端是正常的，以换行隔开（`\r\n`)。  
  直接点击右侧的download下载zip，可能你在windows端看到的就不是以换行隔开的（`\n`)。  
  这是Github造成的。但不会影响程序最后的运行效果。   
  你可以粘贴下面的渠道到channel.txt中保持它在windows端的可读性。

  ```
  samsungapps
  hiapk
  anzhi
  360cn
  xiaomi
  myapp
  91com
  gfan
  appchina
  nduoa
  3gcn
  mumayi
  10086com
  wostore
  189store
  lenovomm
  hicloud
  meizu
  baidu
  googleplay
  wandou
  ```
  也可以自己来写入自己需要的市场，并以换行隔开
- MultiChannelBuildTool.py是多渠道打包的脚本。

## JavaUtil
ChannelUtil.java 用来解析渠道，直接拷贝到Android工程中使用即可。  
ChannelUtil中的getChannel方法可以方便的获取渠道。 

# 常见问题答疑 

这部分问题是由美团大神<a href="http://weibo.com/coderdd" target="_blank" >丁志虎</a>在微博上答复的，摘录如下：

- 这个方案没法解决不同渠道使用渠道自己SDK的问题，友盟的SDK提供了在代码中设置渠道的方式，所以再获取到渠道号后再调用SDK相关设置渠道的方法就可以了
- apk用的是java那一套签名，放在META-INF文件夹里的文件原则上是不参与签名的。如果Google修改了apk的签名规则，这一套可能就不适用了。

# 注意

问：同样一个版本号的2个渠道包，比如先装了360，那么SharedPreferences存的就是360了。这时再用xiaomi渠道的去覆盖安装，那么读出来的渠道号还是360的。不知道博主对这个问题怎么看，还是去掉sp缓存，就保留内存和包中读取？

答：

看你个人的使用场景吧 一般来说 渠道使用无非是统计升级渠道、根据相应渠道变化样式、上报崩溃信息携带渠道。

- 针对1：统计不怎么需要特别情况，你说的这种情况我们也考虑过，但一般用户大多不会这么折腾，也就QA这么玩。
- 针对2：使用flavor来解决了。而不是判断渠道。早期适配魅族手机也是不管渠道，只看是不是魅族手机
- 针对3：这个印象也不大，如果是某渠道包崩溃，少这几个也不会影响。

综上，我们选择不再读取。
当然，如果你有其他使用场景，考量之后觉得要精确，可以每次读包，缓存到内存中。当时我是感觉没有太大必要，才写成这样。

# License

    Copyright 2014 GavinCT

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


