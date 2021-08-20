# FOOD MENU DETECTION





## Dataset
[UEC Food256 Dataset](http://foodcam.mobi/dataset256.html)
```
wget http://foodcam.mobi/dataset256.zip
```

## Convert Food256 Dataset to YOLO format
Please refer to the following directory [food256](./food256)

## Training
### re-organize directories
After converting dataset, my local repository looks like below tree:
```
food_menu_detection/
┣ data_yolo/
┃ ┣ images/
┃ ┃ ┣ train/
┃ ┃ ┗ valid/
┃ ┣ labels/
┃ ┃ ┣ train/
┃ ┃ ┣ valid/
┃ ┃ ┣ train.cache
┃ ┃ ┗ valid.cache
┃ ┗ food_yolo.yaml
┣ food256/
┃ ┣ README.md
┃ ┣ food256.names
┃ ┣ food256_split.ipynb
┃ ┣ food256_to_yolo.ipynb
┃ ┣ make_names.ipynb
┃ ┣ test.txt
┃ ┗ train.txt
┣ yolov5/
┃ ┣ data/
┃ ┣ models/
┃ ┣ runs/
┃ ┣ utils/
┃ ┣ wandb/
┃ ┣ weights/
┃ ┣ Dockerfile
┃ ┣ LICENSE
┃ ┣ README.md
┃ ┣ __init__.py
┃ ┣ detect.py
┃ ┣ hubconf.py
┃ ┣ requirements.txt
┃ ┣ test.py
┃ ┣ train.py
┃ ┣ tutorial.ipynb
┃ ┣ yolov5m.pt
┃ ┣ yolov5s.pt
┃ ┗ yolov5x.pt
┣ README.md
```

### change model.yaml file
change *nc* to 256 in yolov5/models/yolov5*.yaml 

### Training using single gpu
```
python train.py --img 640 --batch 16 --epochs 600 --data ../data_yolo/food_yolo.yaml --weights yolov5s.pt
```

### Training using multipe gpus
```
python -m torch.distributed.launch --nproc_per_node 4 train.py --img 640 --batch 16 --epochs 600 --data ../data_yolo/food_yolo.yaml --weights yolov5s.pt --devices 0,1,2,3 
```

## Results
### Metrics 

### Validation images examples



## DEMO
If you want to watch demo video of menu detection, click the figure below!
[![Food Menu Detection](https://img.youtube.com/vi/2Q8gVsT14Y8/0.jpg)](https://youtu.be/2Q8gVsT14Y8)
