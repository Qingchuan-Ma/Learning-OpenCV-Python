## 一个简单的变换

```python
import cv2
import numpy as np

cv2.namedWindow("Example4-in")
cv2.namedWindow("Example4-out")

img = cv2.imread("test2.png",0)
out = cv2.GaussianBlur(img,(3,3),0)

cv2.imshow("Example4-in",img)
cv2.imshow("Example4-out",out)


cv2.waitKey(0)
cv2.destroyAllWindows()
```
