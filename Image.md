
* opencv image VS PIL image.
```
import cv2
from PIL import Image
import numpy
 
# pil to numpy
img = cv2.cvtColor(np.array(img),cv2.COLOR_RGB2BGR)

# numpy to pil
image = Image.fromarray(cv2.cvtColor(img,cv2.COLOR_BGR2RGB))

```