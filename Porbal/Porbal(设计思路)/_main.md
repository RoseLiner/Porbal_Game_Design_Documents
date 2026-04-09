# Character
## Player
### 视角(Camera)
第三人称

#体验优化 Player可以切换到Ball的视角 (传送时机)   并共享听觉
### 状态
无论是否拿着物品，玩家都能移动或旋转视角
根据玩家**是否拿着物品**分成 (1+2) 种姿态
#### 没拿物品(canDrop = false)
- A *无手持*
#玩法 玩家可以捡起物品
#Unsolved 运动时球不容易被拿起
#### 拿着物品(canDrop = true)
 - B *双手举起*
#玩法 将Ball扔向远处   (exp 投掷手雷)
- B++ 放大远处的场景
#体验优化 保留当前投掷状态瞄准远处   (exp 望远镜，大炮射击)

-  C 脚踢滑板
#玩法 控制Skateboard在地面上的移动   (exp 高尔夫球/保龄球)
将Position置于玩家脚附近

- D 弧形将Baseball在平面抛出(飞牌/香蕉球(足球))
### 瞬移
#玩法 瞬移到主球(BaseBall/Bowling)所在的位置   (Script写球上)
(public Player) #Tip 球和球之间也能传送
#玩法 #Cooldown 标记点后传送
## Ball
### 视角(Camera)
第三人称
#体验优化 Ball可以切换到Player的视角 (Script写球上)
### 状态
**Baseball**和**Porbal**
#### 没拿Baseball(canDrop = true )
- **Baseball**
#玩法 玩家可以将Baseball召唤回身边(is Kinematic = True)
#Improve(施加引力)
#玩法 Baseball可以变成Portalball
#Unsolved 运动时球不容易被拿起
#### 拿着Baseball(canDrop = false && heldObj=Baseball)
 - B *双手举起*
#玩法 将Ball扔向远处   (exp 投掷手雷)
#手感优化 上下左右->右键瞄准镜瞄准
- B++ 放大远处的场景
#体验优化 保留当前投掷状态瞄准远处   (exp 望远镜，大炮射击)

-  C 双手垂下
#玩法 控制Ball在地面上的移动   (exp 高尔夫球/保龄球)
将Position置于玩家脚附近


### 瞬移
#玩法 

#### BaseBall
小球，可以瞬移到Character上
#### Porbal
#玩法 一个比玩家稍大的球形空间，Player可以瞬间进入该空间
进入之后Porbal会变回Baseball
#Colldown Baseball变成Porbal有冷却时间
玩家出现的位置(球视角决定落点/球运动方向后方)

### Physics Material

#### 弹性   
- BaseBall
(Bounsiess=1)碰撞*墙体(Layer=Default)* 能够以原速度弹回
- Bowling
(Bounsiess=0)碰撞后不会往回弹
#Tip 球在地面滚动，贴到有弧度的墙角后会保持原速度飞起
### 辅助
- #体验优化 未抛出时瞄准线显示球抛出后的**运动轨迹 （预测）**

## Skateboard
### 状态
**Skateboard**和**Card**
#### 没拿Skateboard(canDrop = trueo || heldObj = Skateboard)
- **Skateboard**
#玩法 玩家可以将Baseball召唤到身边
#玩法 Baseball可以变成Portalball

#### 拿着Skateboard(canDrop = false && heldObj = Skateboard)
#玩法 玩家可以滑滑板(可以沿地面/墙面(有重力下坠)滑行)
#玩法 可以被玩家以近乎直线的轨迹踢出，
触碰到Collider之后立刻停下
_类似效果，墙离平台比较远是可以先用求传送_
https://www.reddit.com/r/Unity3D/comments/1ro9vyx/tachyon_flow_update_3_improved_overall_ground/
### 瞬移
#玩法 Character可以瞬移到Skateboard上,
瞬移后velocity与Skateboard相同
#玩法 Player可以带着skateboard一起传送到Porbal中
#Unsolved player出现的位置(球视角决定落点/球运动方向后方)
### Physics Material
#Tip 可以短时间吸附在固体表面滑行，可以弹跳
#玩法  玩家可以将滑板投掷出去   (exp   标枪)

### Bugs
#Unsolved 球只能在forward方向被被拿起(PickUp.cs)
![[Pasted image 20260331222126.png]]
#Unsolved 在跳起时砸向地面球会穿过地面
#Unsolved Condition:拿起球，人贴着墙时   Bug:球会穿过墙面
#Unsolved 球往墙缝里扔，会卡在墙里(调整Collider)
#Unknown_few Condition: 拿起球砸向墙面，跟随球，球到了墙角，
Bug: 球快速旋转飞起， 人把球挤到墙角，
人跟随球快速飞起(可能是人踩球上了)
Condition:靠近墙跳跃在空中快速捡球扔球
Bug:人快速飞起

# main
### 玩家可以做什么
- 扔Ball
- 扔Skateboard
- 传送到Ball/Skateboard
- 移动/跳跃/爬坡
### Steps
(观察)光影,声音,地形 -> (规划)找到通关条件,->
### 跑酷元素
玩家可以在特定的地方滑行Skateboard感受世界
(*限制滑行区域防止关卡解谜太容易被解决*)

# New
## Curve

## Material

### Collider
### Bounciance

### Friction


## Force
### Centrifugal Force

### Gravity


## Space
### Velority


### Attack Range


### Obtacle

### Shape

### Rotate
## Time

## Light


# Parallel
不用捡东西
Skateboard~velocity
Baseball~height+复杂地形的Direction
# UI
## 按键控制
### Player
#### General
- *Keyboard WASD*   移动
- *KeyBoard Space*   跳跃
- *Mouse Axis*   旋转视角

#### canDrop = false
- *Keyboard E*   捡起Ball
（ #PlanB #体验优化 直接将Ball召回到手上）

#### canDrop = true
- *Keyboard R*   按住时旋转视角物品也会旋转
#手感优化 
#Tip 如果设置球可以往固定方向旋转后抛出，
玩家搓球提供初速度

- *KeyBoard F* #玩法 瞬移到主球的位置
- *Mouse ScrollWheel*   (状态B)调整力度/(状态B++)放大远处场景
（ #PlanB \[Settings\]*Keyboard Space*按键静态调整力度
( Y解谜或跑图   N战斗)）

- Keyboard Q   切换状态 (A/B/C)
- KeyBoard Z   切换主球(BaseBall)
