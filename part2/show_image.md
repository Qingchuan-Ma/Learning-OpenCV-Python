# 显示图像


例 2-1：用于从磁盘加载并在屏幕上显示一幅图像的简单 OpenCV 程序
```python
import cv2
import numpy as np

img = cv2.imread('test2.png',0)
cv2.namedWindow("Example",cv2.WINDOW_AUTOSIZE)
cv2.imshow('Example',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```



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
