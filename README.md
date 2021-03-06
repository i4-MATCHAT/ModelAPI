# Model-API

### ๐ YOLOv5 Model

- ์ค๊ณ ๊ฑฐ๋ ์ํ์ ์ข๋ฅ๋ฅผ ํ๋ณํ๊ธฐ ์ํด YOLOv5 ๋ชจ๋ธ์ ์ปค์คํฐ๋ง์ด์ง ํ ํ Object Detection์ ์งํ

- Yolov5 Model : https://github.com/ultralytics/yolov5 



### ๐ ๋ฐ์ดํฐ ๋ผ๋ฒจ๋ง

- ํฌ๋กค๋ง์ ํตํด ์ํ ์ด๋ฏธ์ง ๋ฐ์ดํฐ ์์ง
- ๋ผ๋ฒจ๋ง Tool : [Makesense](https://www.makesense.ai/)
- converse high, nike daybreak 2๊ฐ์ class๋ก ํ์ต


### ๐ ๋ฐ์ดํฐ์ 

- cocoval2017 : https://drive.google.com/file/d/1fR5rPbnFA82-beYaUAZIq1oNlQGvSLky/view?usp=sharing <br>
- cocotest2017 : https://drive.google.com/file/d/1fR5rPbnFA82-beYaUAZIq1oNlQGvSLky/view?usp=sharing <br>
- ์ ์ฒด ๋ฐ์ดํฐ : https://drive.google.com/file/d/1gVNf6pIyMxyrRfLySIvLiV_XDk7viJb_/view?usp=sharing

### ๐ ํ์ต ์งํ

๋ค์๊ณผ ๊ฐ์ ๊ณผ์ ์ผ๋ก ์ปค์คํ ๋ชจ๋ธ ํ์ต ์งํ

#### - yaml ํ์ผ ์ค์ 

custom_data.yaml ํ์ผ์ ๋ค์๊ณผ ๊ฐ์ด ์ค์ 
```python
# Train/val/test sets as 1) dir: path/to/imgs, 2) file: path/to/imgs.txt, or 3) list: [path/to/imgs1, path/to/imgs2, ..]
path: ../train_data/  # dataset root dir
train: images/train  # train images (relative to 'path') 128 images
val: images/val  # val images (relative to 'path') 128 images
test:  # test images (optional)

# Classes
nc: 2  # number of classes
names: ['converse high', 'nike daybreak']  # class names
```

#### - ์ ๋ชจ๋ธ ์ค์น ๋ฐ ํ๊ฒฝ ์ค์ 
```python
!git clone https://github.com/ultralytics/yolov5  # clone
%cd yolov5
%pip install -qr requirements.txt  # install

import torch
from yolov5 import utils
display = utils.notebook_init()  # checks
```
#### - ์ปค์คํ ๋ฐ์ดํฐ ์๋ก๋ ๋ฐ ์์ถ ํด์ 
```python
!unzip -q ../train_data.zip -d ../content/
```

#### - ๋ชจ๋ธ ํ์ต ์งํ
```python
!python train.py --img 640 --batch 16 --epochs 700 --data custom_data.yaml --weights yolov5s.pt --cache
```

#### - test ์ด๋ฏธ์ง detection
```python
!python detect.py --weights runs/train/exp/weights/last.pt --img 640 --conf 0.35 --source ../test/
```

#### - detection ๊ฒฐ๊ณผ ์ด๋ฏธ์ง

![1](https://i.postimg.cc/wv3qNrgZ/1-r.jpg)

![2](https://i.postimg.cc/v8g9Fqf0/2-r.png)


