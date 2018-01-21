# 初试牛刀——显示图像


例 2-1：用于从磁盘加载并在屏幕上显示衣服图像的简单 OpenCV 程序
```
import cv2
import numpy as np

img = cv2.imread('test2.png',0)
cv2.namedWindow("Example",cv2.WINDOW_AUTOSIZE)
cv2.imshow('Example',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
