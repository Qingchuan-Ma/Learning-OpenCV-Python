## 显示图像

OpenCV 开发包提供了读取各种类型的图像文件、视频肥荣以及摄像机输入的功能，这些功能是 OpenCV 开发包中所包含的 HighGUI 工具集中的一部分。我们将使用其中的一些功能编写一段简单的程序，用于读取并在屏幕上显示一张图像，如例 2-1 所示。

例 2-1：用于从磁盘加载并在屏幕上显示一幅图像的简单 OpenCV 程序
```python
import cv2
import numpy as np

img = cv2.imread('example.png',0)
cv2.namedWindow("Example",cv2.WINDOW_AUTOSIZE)
cv2.imshow('Example',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
以上程序执行时，该程序将向内存加载一幅图像，并将该图像显示于屏幕上，直至按下键盘的任意一个键以后它才关闭窗口并退出程序，下面我们将对以上代码做逐行分析，并仔细讲解每个函数的用法以帮助读者理解这段程序。
```python
import cv2
import numpy as np
```
这两行程序的功能是导入 opencv-python 和 NumPy 模块。
```python
img = cv2.imread('example.png')
```
该行程序的功能是将图像文件加载至内存。cv2.imread() 函数是一个高层调用接口，它通过文件名确定文件进而通过文件头信息确定被加载文件的格式；并且该函数将自动分配图像数据结构所需的内存。需要指出的是，cv2.imread() 现在支持的文件类型包括 bmp, dib, jpeg, jpg, jpe, jp2, png, webp, pbm, pgm, ppm, sr, ras, tiff, tif。以后我们可以知道，该函数执行完以后将图像数据以 NumPy 的 array 形式存入变量 img。OpenCV 使用该数据类型处理诸如单通道(single-channel)、多通道(multichannel)、整型(integer-valued)、浮点型的(floating-point-valued)等所有类型的图像文件。
```python
cv2.namedWindow("Example",cv2.WINDOW_AUTOSIZE)
```
cv2.namedWindow() 也是一个高层调用接口，该函数由 HighGUI 库提供，用于在屏幕上创建一个窗口，将被显示的图像包含于该窗口中。函数的第一个参数指定了该窗口的窗口标题（本例中为"Example"），如果要是用 HighGUI 库所提供的其他函数与该窗口进行交互时，我们将通过该参数值引用这个窗口。

cv2.namedWindow() 函数的第二个参数定义了窗口的属性。该参数可被设置为 0 或 cv2.WINDOW_AUTOSIZE 等，设置为 0 时，窗口的大小不会因图像的大小而改变，图像只能在窗口中根据窗口的大小进行拉伸或缩放；而设置为 cv2.WINDOW_AUTOSIZE 时，窗口会根据图像的实际大小自动进行拉伸或缩放，以容纳图像。
```python
cv2.imshow('Example',img)
```
只要有一个与某个图像文件相对应的 array，我们就可以在一个已创建好的窗口（使用 cv2.namedWindow()）中使用 cv.imshow() 函数显示该图像。

asjdhasjkdhaskjdhasjkdhasjkdhasjkhaskjh


```python
import cv2
import numpy as np

img = cv2.imread('test2.png',0)
cv2.namedWindow("Example",cv2.WINDOW_AUTOSIZE)
cv2.imshow('Example',img)
k = cv2.waitKey(0)
if k == 27:
    cv2.destroyAllWindows()
elif k == ord('s'):
    cv2.imwrite('messigray.png',img)
    cv2.destroyAllWindows()
else:
    cv2.destroyAllWindows()
```
