# 播放 AVI 视频


```python
import cv2
import numpy as np

cv2.namedWindow("Example2",cv2.WINDOW_NORMAL)
cap = cv2.VideoCapture("test.avi")

while(cap.isOpened()):
    ret,frame = cap.read()
    if ret == False:
        break
    cv2.imshow("Example2",frame)
    press_key = cv2.waitKey(33)
    if press_key & 0xFF == ord('q'):
        break
    if press_key == 27:
        break

cap.release()
cv2.destroyWindow("Example2")
```
