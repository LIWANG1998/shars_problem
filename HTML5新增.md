1、结构标签
 （1）section：独立内容区块，可以用h1~h6组成大纲，表示文档结构，也可以有章节、页眉、页脚或页眉的其他部分；
 （2）article：特殊独立区块，表示这篇页眉中的核心内容；
 （3）aside：标签内容之外与标签内容相关的辅助信息；
 （4）header：某个区块的头部信息/标题；
 （5）hgroup：头部信息/标题的补充内容；
 （6）footer：底部信息；
 （7）nav：导航条部分信息
 （8）figure：独立的单元，例如某个有图片与内容的新闻块。

2、表单标签
 （1）email：必须输入邮件；
 （2）url：必须输入url地址；
 （3）number：必须输入数值；
 （4）range：必须输入一定范围内的数值；
 （5）Date Pickers：日期选择器
 （6）search：搜索常规的文本域；
 （7）color：颜色；

3、媒体标签
 （1）video：视频
 （2）audio：音频
 （3）embed：嵌入内容（包括各种媒体），Midi、Wav、AU、MP3、Flash、AIFF等。

H5新增属性
 （1）对于js进行添加的属性



```xml
<script defer src=".....js" onload="alert('a')"></script> 
<script async src=".....js" onload="alert('b')"></script> 
```

异步加载先出现b再出现a。
 （2）网页中标签中加入小图标的样式代码
 有序列表ol:新增start（列表起始值），reversed（是否倒置）menu菜单type属性（3个菜单类型）
 内嵌css样式：在标签内部来定义一个样式区块（scoped）,只对样式标签内部才有效
 内嵌框架：iframe元素，新增了seamless无边距无边框，srcdoc定义了内嵌框架的内容。

总结新增属性：
 （1）manifest属性：定义页面需要用到的离线应用文件，一般放在<html>标签里
 （2）charset属性：meta属性之一,定义页面的字符集
 （3）sizes属性： ``新增属性，当link的rel="icon"时，用以设置图标大小
 （4）base属性: ``表示当在新窗口打开一个页面时，会将href中的内容作为前缀添加到地址前
 （5）defer属性：script标签属性，表示脚本加载完毕后，只有当页面也加载完毕才执行（推迟执行）
 （6）async属性：script标签属性，脚本加载完毕后马上执行（运行过程中浏览器会解析下面的内容），即使页面还没有加载完毕（异步执行）
 （7）media属性： ``元素属性：表示对何种设备进行优化
 （8）hreflang属性： ``的属性，表示超链接指向的网址使用的语言
 （9）ref属性：``的属性,定义超链接是否是外部链接
 （10）reversed属性:``的属性，定义序号是否倒叙
 （11）start属性：``的属性，定义序号的起始值
 （12）scoped属性：内嵌CSS样式的属性，定义该样式只局限于拥有该内嵌样式的元素，适用于单页开发。