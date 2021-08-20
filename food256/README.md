# Convert raw Food256 dataset to YOLO format

1. run make_names.ipynb
    - make Food256.names file
2. run food256_to_yolo.ipynb 
    - imports bb_info.txt from the image directory for each class and creates individual bbox files
3. run food256_split.ipynb
    - split all images into train.txt for training image list and test.txt for validating image list.
