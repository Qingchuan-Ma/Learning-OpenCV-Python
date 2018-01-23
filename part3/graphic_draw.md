## 绘图

我们经常需要绘制图像或者在已有的图像上方绘制一些图形。为此，OpenCV 提供了一系列的函数帮助我们绘制直线、方形和圆形等。

### 直线和矩形

cv2.line() 是绘图函数中最简单的，只需用 Bresenham 算法[Bresenham65]画一条线：
```python
cv2.line(img, pt1, pt2, color[, thickness[, lineType[, shift]]]) -> line
```
该函数的第一个参数是 img，是使用 cv2.imread() 读取图片获得的返回值或者是利用 NumPy 定义的 ndarray 数组。

随后两个参数是两个 CvPoint 数据类型，定义直线的起始点和终止点。

下一个参数是 CvScalar 类型的颜色变量。应该注意的 Color 的 4 个分量按照 BGRA 的顺序排列。

接下来的三个属性是可选的。
1. thickness 是线的粗细（像素），类型为 int。
2. lineType 是线的种类，分为 LINE_8(default), LINE_4, LINE_AA(antialiased line)。前者是 8 连通线条，较为平滑且不会走样，第二者是 4 连通线条，斜线会产生重叠以至于看上去过于粗重，不过画起来速度要快得多，相比前两者使用的 Bresenham 算法，后者是使用高斯滤波绘制反锯齿线。
3. shift 是在点坐标上的小数部分。

cv2.rectangle() 和 cv2.line() 几乎同样便捷。cv2.rectangle() 用于画矩形。他和 cv2.line() 接受的参数一致，因此产生的矩形总是平行于 X 和 Y 轴。利用 cv2.rectangle()，我们只需要给出两个对顶点，OpenCV 便可画出一个矩形。下面是其定义:
```python
cv2.rectangle(img, pt1, pt2, color[, thickness[, lineType[, shift]]]) -> img
```

### 圆形和椭圆

画圆同样简单，其参数与前面类似。
```python
cv2.circle(img, center, radius, color[, thickness[, lineType[, shift]]]) -> img
```
对于圆形和矩形等很多封闭图形来说，thickness 参数也可以设置为 cv2.FILLED，其值是 < 0；其结果是使用与边一样的颜色填充圆内部。

椭圆函数比 cv2.circle 略微复杂一些：
```python
cv2.ellipse(img, center, axes, angle, startAngle, endAngle, color[, thickness[, lineType[, shift]]]) -> img
cv2.ellipse(img, box, color[, thickness[, lineType]]) -> img
```
未完待续
