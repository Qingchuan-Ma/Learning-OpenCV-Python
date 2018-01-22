## 视频播放控制

```python
import cv2
import numpy

g_slider_position = 0
cap = cv2.VideoCapture("ss霸体机甲死士 生八打.avi")

def onTrackbarSlide(pos):
    if isinstance(pos,int):
        cap.set(cv2.CAP_PROP_POS_FRAMES,pos)
    else:
        return False


cv2.namedWindow("Example3",cv2.WINDOW_NORMAL)

frames = int(cap.get(cv2.CAP_PROP_FRAME_COUNT))
if frames != 0:
    cv2.createTrackbar("Position","Example3",g_slider_position,frames,onTrackbarSlide)

while(cap.isOpened()):
    ret,frame = cap.read()
    if ret == False:
        break
    g_slider_position = int(cap.get(cv2.CAP_PROP_POS_FRAMES))
    cv2.setTrackbarPos("Position","Example3",g_slider_position)
    cv2.imshow("Example3",frame)
    press_key = cv2.waitKey(33)
    if press_key & 0xFF == ord('q'):
        break
    if press_key == 27:
        break

cap.release()
cv2.destroyAllWindows()
```
