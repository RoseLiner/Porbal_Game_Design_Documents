## Player

### 状态
无论是否拿着物品，玩家都能移动或旋转视角
根据玩家**是否拿着物品**分成 (1+2) 种姿态
#### 拿着物品(canDrop = false)
- A *无手持*
#玩法 玩家可以捡起物品
#### 没拿物品(canDrop = true)
 - B *双手举起*
#玩法 将Ball扔向远处   (exp 投掷手雷)
- B++ 放大远处的场景
#体验优化 保留当前投掷状态瞄准远处   (exp 望远镜，大炮射击)

-  C 双手垂下
#玩法 控制Ball在地面上的移动   (exp 高尔夫球/保龄球)

## Ball
### 辅助
- #体验优化 未抛出时瞄准线显示球抛出后的**运动轨迹 （预测）**

## 按键控制
### Player
#### General
- *Keyboard WASD*   移动

- *Mouse Axis*   旋转视角

#### canDrop = false
- *Keyboard E*   捡起Ball
（ #PlanB #体验优化 直接将Ball召回到手上）

#### canDrop = true
- *Keyboard R*   按住时旋转视角物品也会旋转
#手感优化

- *Mouse ScrollWheel*   (状态B)调整力度/(状态B++)放大远处场景
（ #PlanB \[Settings\]*Keyboard Space*按键静态调整力度
( Y解谜或跑图   N战斗)）

- Keyboard Q   切换状态 (A/B/C)