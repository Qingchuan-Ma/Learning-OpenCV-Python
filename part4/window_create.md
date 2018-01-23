## 创建窗口

首先，我们要做的是利用 HighGUI 将一副图像显示到屏幕上。我们使用 cv2.namedWindow() 来实现这个功能。这个函数接受两个参数，第一个参数用来表示新窗口的名字，这个名称显示在窗口的顶部，同时用作 HighGUI 中其他函数调用窗口的句柄。第二个参数是一个标志，用来表示是否需要使窗口大小自动适应读入的大小。下面是这个函数的定义：
```python
cv2.namedWindow(winname[, flags]) -> None
```
需要留意的是参数 flags，到目前为止，唯一有效的设置是 0 或者 cv2.WINDOW_AUTOSIZE。如果使用 cv2.WINDOW_AUTOSIZE，HighGUI 会根据图像的大小调整窗口大小。这样，窗口大小会随着图像的载入而根据图像大小调整，用户没办法手动调整窗口大小。当然，如果不想窗口大小自动调整，也可以将参数值设置为 0，这样的话，用户就可以随意调整窗口的大小了。不仅如此，该参数值还有其他可选:
1. cv2.WINDOW_NORMAL 或 cv2.WINDOW_AUTOSIZE
2. cv2.WINDOW_FREERATIO 或 cv2.WINDOW_KEEPRATIO
3. cv2.WINDOW_GUI_NORMAL 或 cv2.WINDOW_GUI_EXPANDED
4. cv2.WINDOW_FULLSCREEN 和 cv2.WINDOW_OPENGL

具体区别请查看第一章概述中的 api 文档。默认该参数 flags == cv2.WINDOW_AUTOSIZE | cv2.WINDOW_KEEPRATIO | cv2.WINDOW_GUI_EXPANDED

当窗口被创建以后，我们通常是想加入一些东西到里面。不要着急，在做那些事情以前，我们先看看当不需要这些窗口时，如何释放他们。为了释放窗口，我们需要使用 cv2.destroyWindow()，这个函数接受一个字符串参数，这个字符串是窗口创建时所指定的名字。

在 OpenCV 中，窗口根据名称来引用（操作系统独立的）而不是一些“不友好”的句柄。句柄与窗口名称的转换都由 HighGUI 在后台处理，我们不用为这些问题操心。不仅如此，在 OpenCV3 中，在 OpenCV1 中有的 cvGetWindowHandle(), cvGetWindowName() 等函数已被删除。

此外， HighGUI 提供了 cv2.resizeWindow() 用来调整窗口的大小：
```python
resizeWindow(winname, width, height) -> None
```
这里在宽度与高度是以像素为单位的，指定了窗口中可以显示部分（这部分的大小可能才是真正关心的）大小。
