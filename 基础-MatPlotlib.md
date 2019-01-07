# 基础-MatPlotlib

[TOC]

### 1.概念

绘图操作,数据图形化



### 2.使用

```python
import matplotlib as plt #引入matplotlib包

show() #通用,显示图片
```



##### 方法列表

```python
#图像的读取与现实
plt.imread(图) #数组矩阵的形式读取图片
plt.imshow(图) #显示图片

```



### 3.绘图plot

##### 方法列表

```python
#横坐标一般是任意类型列表,纵坐标可以使用方程替代,并且根据纵坐标节点设置动态扩展坐标显示
plt.plot([横坐标轴],[纵坐标轴],str,scalex=True,scaley=True,**kwargs) #横坐标,纵坐标,显示颜色类型,默认‘b-’,显示详细横坐标,显示详细纵坐标,各种属性
plt.axis([x0,x1,y0,y1])#4个参数,指定坐标轴尺寸,列表前两位表示x轴范围,后两位表示y轴范围
plt.xlabel(横坐标信息)
plt.ylabel(纵坐标信息)
plt.title(抬头信息)

plt.setp(line2D,**kwargs) #MATLAB风格设置plot属性,如color=‘y’,linewidth=2.0

plt.figure(1) #第一个图形,参数为图形的整个框架
plt.subplot(321) #第一个图形的第一个子图,参数: 3为子图容量,2为子图横向显示个数,1为子图顺序

plt.clf() #清空整个图形
plt.cla() #清空当前轴域
```



##### 属性列表

```python
linewidth=int #设置线条宽度
```



##### 图形颜色和类型列表

颜色

| character | color   |
| --------- | ------- |
| ‘b’       | blue    |
| ‘g’       | green   |
| ‘r’       | red     |
| ‘c’       | cyan    |
| ‘m’       | magenta |
| ‘y’       | yellow  |
| ‘k’       | black   |
| ‘w’       | white   |

线条显示类型

| character | description           |
| --------- | --------------------- |
| `'-'`     | solid line style      |
| `'--'`    | dashed line style     |
| `'-.'`    | dash-dot line style   |
| `':'`     | dotted line style     |
| `'.'`     | point marker          |
| `','`     | pixel marker          |
| `'o'`     | circle marker         |
| `'v'`     | triangle_down marker  |
| `'^'`     | triangle_up marker    |
| `'<'`     | triangle_left marker  |
| `'>'`     | triangle_right marker |
| `'1'`     | tri_down marker       |
| `'2'`     | tri_up marker         |
| `'3'`     | tri_left marker       |
| `'4'`     | tri_right marker      |
| `'s'`     | square marker         |
| `'p'`     | pentagon marker       |
| `'*'`     | star marker           |
| `'h'`     | hexagon1 marker       |
| `'H'`     | hexagon2 marker       |
| `'+'`     | plus marker           |
| `'x'`     | x marker              |
| `'D'`     | diamond marker        |
| `'d'`     | thin_diamond marker   |
| `'|'`     | vline marker          |
| `'_'`     | hline marker          |

##### 默认扩展纵坐标

```python
plt.plot([-1,0,1,2,3],(2,3,3,3,3))
plt.xlabel("Width😊")
plt.ylabel("Height")
plt.title("😫TITLE😢")
plt.show()
```



![image-20190105113154039](https://ws1.sinaimg.cn/large/006tNc79gy1fyvjvdyrgtj30hs0dc74m.jpg)

##### 手动指定纵坐标

```python
plt.plot([100,200,300,450,250,250,300,400,500],'y--') #指定数据或公式变量,字符串控制颜色和类型
plt.axis([0,10,0,500]) 
plt.xlabel("Width😊")
plt.ylabel("Height")
plt.title("😫TITLE😢")
plt.show()
```

![image-20190105120002463](https://ws3.sinaimg.cn/large/006tNc79gy1fyvkolmhg9j30hs0dc3yz.jpg)

![image-20190105120032817](https://ws2.sinaimg.cn/large/006tNc79gy1fyvkp4i4ksj30hs0dcq35.jpg)



##### 多线显示

```python
t=np.arange(0.,5.,0.2)
plt.plot(t,t,'y-',t,t*2,'ro',t,t*t,'g^') #每根线条的第一个参数设置指定线条的宽度
plt.show()
```

![image-20190105124204205](https://ws1.sinaimg.cn/large/006tNc79ly1fyvlwczuemj30hs0dcdg4.jpg)





##### 加粗显示

```python
plt.plot([100,112,211,233,222,111,200,260],linewidth=3)
plt.axis([0,10,0,300])
plt.show()
```

![image-20190105124614560](https://ws1.sinaimg.cn/large/006tNc79ly1fyvm0ow3vdj30hs0dc0t4.jpg)



##### Line2D实例

plot的返回对象,Line2D

```python
line1,=plt.plot([100,112,211,233,222,111,200,260])
plt.axis([0,10,0,300])
plt.show()
```



方法列表

| 属性                     | 值类型                                        |
| ------------------------ | --------------------------------------------- |
| `alpha`                  | 浮点值                                        |
| `animated`               | `[True / False]`                              |
| `antialiased or aa`      | `[True / False]`                              |
| `clip_box`               | `matplotlib.transform.Bbox` 实例              |
| `clip_on`                | `[True / False]`                              |
| `clip_path`              | `Path` 实例， `Transform`，以及`Patch`实例    |
| `color or c`             | 任何 `matplotlib` 颜色                        |
| `contains`               | 命中测试函数                                  |
| `dash_capstyle`          | `['butt' / 'round' / 'projecting']`           |
| `dash_joinstyle`         | `['miter' / 'round' / 'bevel']`               |
| `dashes`                 | 以点为单位的连接/断开墨水序列                 |
| `data`                   | `(np.array xdata, np.array ydata)`            |
| `figure`                 | `matplotlib.figure.Figure` 实例               |
| `label`                  | 任何字符串                                    |
| `linestyle` or `ls`      | `[ '-' / '--' / '-.' / ':' / 'steps' / ...]`  |
| `linewidth` or `lw`      | 以点为单位的浮点值                            |
| `lod`                    | `[True / False]`                              |
| `marker`                 | `[ '+' / ',' / '.' / '1' / '2' / '3' / '4' ]` |
| `markeredgecolor or mec` | 任何 `matplotlib` 颜色                        |
| `markeredgewidth or mew` | 以点为单位的浮点值                            |
| `markerfacecolor or mfc` | 任何 `matplotlib` 颜色                        |
| `markersize or ms`       | 浮点值                                        |
| `markevery`              | `[ None / 整数值 / (startind, stride) ]`      |
| `picker`                 | 用于交互式线条选择                            |
| `pickradius`             | 线条的拾取选择半径                            |
| `solid_capstyle`         | `['butt' / 'round' / 'projecting']`           |
| `solid_joinstyle`        | `['miter' / 'round' / 'bevel']`               |
| `transform`              | `matplotlib.transforms.Transform` 实例        |
| `visible`                | `[True / False]`                              |
| `xdata`                  | `np.array`                                    |
| `ydata`                  | `np.array`                                    |
| `zorder`                 | 任何数值                                      |



##### 多子图显示

```
t=np.arange(0,5,0.1)
plt.figure(1)
plt.subplot(321)
plt.plot(t,t*t,'y-',t,t*t,'go')
plt.subplot(322)
plt.plot(t,t*3,'y-',t,t*3,'go')
plt.subplot(313)
plt.plot(t,t*3,'y-',t,t*3,'go')
plt.show()
```

