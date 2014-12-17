AndroidMultiChannelBuildTool
============================

安卓多渠道打包工具。   
实现思路讲解： [Android批量打包提速 - GavinCT](http://www.cnblogs.com/ct2011/p/4152323.html)  

使用本工具，Android程序员仅需将ChannelUtil.java放入到工程里使用，以后打包的事情就不用自己动手了。  
安装个Python环境，双击一下MultiChannelBuildTool.py，谁都可以打包了！
# 目录介绍及使用注意
## PythonTool
Python2 与 Python3 都能正常使用 

- info目录下的channel用来存放渠道，多个渠道之间用换行隔开。
- MultiChannelBuildTool.py是多渠道打包的脚本。

## JavaUtil
ChannelUtil.java 用来解析渠道，直接拷贝到Android工程中使用即可。  
ChannelUtil中的getChannel方法可以方便的获取渠道。 


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


