### 矩阵

> matrix()	3x3<br/>
> matrix3d()	4x4

```
transform: matrix(a, b, c, d, e, f)
// |a c e|    |x|   |ax + cy + e|
// |b d f| .  |y| = |bx + dy + f|
// |0 0 1|    |1|   |0 +  0  + 1|
```

```
// 最后两个参数是x y方向位移参数
transform matrix(1, 0, 1, 30, 30)
// 其中ax + cy + e为变换后的水平坐标
// bx + dy + f表示变换后的垂直坐标
// x y为元素偏移中心
// 2d位移中只关心最后两个参数即可分别为位移后x y坐标
```

```
// 第一个和第二个参数是x y方向缩放参数
matrix(s, 0, 0, s, 0, 0)
x' = ax+cy+e = s*x+0*y+0 = s*x
y' = bx+dy+f = 0*x+s*y+0 = s*y
```

```
// 旋转则使用三角函数
matrix(cosθ,sinθ,-sinθ,cosθ,0,0)
x' = x*cosθ-y*sinθ+0 = x*cosθ-y*sinθ
y' = x*sinθ+y*cosθ+0 = x*sinθ+y*cosθ
```

```
// 拉伸
matrix(1,tan(θy),tan(θx),1,0,0)
x' = x+y*tan(θx)+0 = x+y*tan(θx) 
y' = x*tan(θy)+y+0 = x*tan(θy)+y
```