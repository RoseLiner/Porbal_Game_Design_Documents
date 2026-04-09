# Velocity

### direction


# +++
## Porbal
### 简化机制
- Space
##### 无重力(水平方向上移动时)
将原空间看为一个元(**1**)
Clone(**1->1,1**)+在传送门处拼接(**++**)
... (+1+) (+1+) (+1+) ...
![](img_v3_0210i_15c34769-8013-4064-be93-6dea168b67fg.jpg)

**空间不是分离的，传送门能到达的地方玩家也能到达**
- Velocity
传递Velocity,改变Direction

![](img_v3_0210i_823815e9-ed09-43a6-a9af-422ab63d69bg.jpg)

- Camera
玩家有了更广的视角

### World (元之间千丝万缕的联系)
> **position和Velority不是相互独立的**

#### Velocity的矢量叠加
- position之间有高度差 -> 重力方向上会叠加新的Velocity分量
 ![](img_v3_0210i_e63afbbf-ce9a-4b3f-9033-81b747bbe51g.jpg)
蓝色箭头代表原速度(Velocity0)，绿色箭头代表重力带来的新速度矢量
以红点为圆心，Velocity0为半径的圆
叠加后的Velocity->以圆上任意一点为起点，红点为重点的速度矢量
**高度越高/Velocity0越小，红点偏移越明显**
##### 重力势能 -> 动能
> **高处的物体下落会增大速度**
- 获得初速度
- 获得更大的速度
![](img_v3_0210i_11b00147-ab9d-4d8a-8df4-5850c809e4cg.jpg)


> 那么问题来了，更大的速度有什么用呢？

**同样的下落时间跳得更远**
![](img_v3_0210i_548d90b6-cff9-47ff-b453-c9c176565fag.jpg)

> 高度差 -> 更快的速度 -> 更远的位移
- 我们可以先用传送门改变direction，然后借助高度差获取velocity

![[img_v3_0210i_c612a007-9961-4bfc-8195-cf12b8bab61g.jpg]]


##### 矢量叠加 -> direction改变
![](img_v3_0210i_e63afbbf-ce9a-4b3f-9033-81b747bbe51g.jpg)
圆上的点指向圆心是Velocity0，指向红点的就是叠加后的Velocity