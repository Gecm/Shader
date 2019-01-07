# Shader
shader water

https://blog.csdn.net/puppet_master/article/details/52975666 博客地址


简单地说就是向Fragment Shader传入三个uniform值startPos(鼠标点击位置即扩散起始位置)、curdis(波纹扩散的距离)、time(时间)，去控制像素的偏移量，里面的常量参数可以自己去调整。

对于creator使用shader需要注意的点
动态合图
在creator2.0中加入的动态合图会在运行时将多张图片合成一张大图，该功能会影响自定义shader的使用。所以需要这行代码关闭这个功能 cc.dynamicAtlasManager.enabled = false;
https://docs.cocos.com/creator/manual/zh/advanced-topics/dynamic-atlas.html4

资源延迟加载
当资源延迟加载时需要注意使用自定义shader的时间点会不会被资源延迟加载影响，例如当某个prefab使用资源延迟加载，而在与该prefab绑定的脚本的start()中使用自定义shader，此时因为延迟加载的缘故会使内置shader覆盖自定义shader。
