为Rime输入法添加Emoji表情-精简版本
=================

项目介绍  
-----------------
本项目是对@rtransformation项目rime-opencc_emoji_symbols的修改  
原项目地址： https://github.com/rtransformation/rime-opencc_emoji_symbols  
将原项目中Emoji同一人物类5个不同肤色版本简化成1个  
并把不需要的以及个人不常使用的部分去除，提高全拼打字时的选择效率  

系统版本
-----------------
系统：macOS Monterey 12.1

使用方法
-----------------
1️⃣  
将es.txt和es.json放入Rime输入法的opencc文件夹下。  
在你所使用的方案的xxxx.schema.yaml文件的「相应」位置加入如下代码（注意缩进）：  
````
switches:
  - name: show_es
    reset: 1
    states: [ 😔, 😀 ]

engine:
  filters:
    - simplifier@es_conversion

es_conversion:
  opencc_config: es.json
  option_name: show_es
 ````
2️⃣  
（来自原项目issue中@raawaa提供的方法，未测试）   
https://github.com/rtransformation/rime-opencc_emoji_symbols/issues/6  
原文：  
“如果是使用custom文件patch的方式配置可以这么写，在这里贴出来看看有没有参考价值。”  
````
patch:
  switches/@next:
    name: show_es
    reset: 1
    states: [ 😔, 😀 ]
  'engine/filters/@before 0':
    simplifier@es_conversion
  es_conversion:
    opencc_config: es.json
    option_name: show_es
    tips: all
````
