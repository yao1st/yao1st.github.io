---
title: matplotlib多图片无阻塞显示
date: 2017-12-20 10:38:46
tags: -python
categories: python
password:
visible:
---
想用matplotlib实现类似Matlab的图片显示效果。

参考[StackOverflow](https://stackoverflow.com/questions/458209/is-there-a-way-to-detach-matplotlib-plots-so-that-the-computation-can-continue)

如果不是用IPython，直接采用``block=False``属性的话，图片会一闪而过。

采用多线程倒不失为一个好方法。

``ion()``进入交互模式的方法，则比较适用于同一函数下的操作。个人觉得不好用。

最后采用的方法是利用``draw()``函数。

**子函数中返回一个figure对象``fig``,然后在主函数中利用``draw()``函数依次等待，这样最后再``plt.show()``让所有图片统一显示。但是这种方法本质还是阻塞的，适合在脚本最后一齐显示所有图片。**