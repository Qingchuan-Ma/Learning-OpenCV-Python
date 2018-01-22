## 写入 AVI 视频文件

```python
import cv2
import numpy as np

def onChange(pos):
    return False

g_slider_position = 0
cap = cv2.VideoCapture("ss霸体机甲死士 生八打.avi")

fourcc = cv2.VideoWriter_fourcc(*'DIVX')
out = cv2.VideoWriter("output.avi",fourcc, 20.0, (640,480))

cv2.namedWindow("Process",cv2.WINDOW_NORMAL)

frames = int(cap.get(cv2.CAP_PROP_FRAME_COUNT))
if frames != 0:
    cv2.createTrackbar("Position","Process",g_slider_position,frames,onChange)

while(cap.isOpened()):
    ret, frame = cap.read()
    if ret==True:
        gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
        g_slider_position = int(cap.get(cv2.CAP_PROP_POS_FRAMES))
        out.write(gray)
        cv2.setTrackbarPos("Position","Process",g_slider_position)
        cv2.imshow('Process',gray)
        if cv2.waitKey(1) & 0xFF == ord('q'):
            break
        if cv2.waitKey(1) & 0xFF == 27:
            break
    else:
        break

cap.release()
out.release()
cv2.destroyAllWindows()
```
