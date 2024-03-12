# Trash Classification

Trash classification is the process of sorting waste materials into distinct categories.

## Members

Name | StudentID
------------- | -------------
นาย วิทวัส ประพันธ์วงศ์  | 6410450265 
นาย ปาณชัย คชกาษร | 6410450176 
นางสาว ธัญวราลี ธเนศธรรมโรจน์ | 6410450150


## Directories purpose

Dir | Purpose
------------- | -------------
Our_Data |  folder นี้ไว้เก็บไฟล์ data ที่ทำการหามาเอง
docs | folder นี้ไว้เก็บ doc และ presentation pdf ของ project
sandbox | folder นี้ไว้เก็บการทดลอง code ต่างๆ รวมถึงการเทรน model
src | folder เก็บตัวงาน final ของ project



## Installation

Use the package manager pip to install after making an environment with anaconda.

```bash
conda create --name dl_env python=3.10
conda activate dl_env
conda install -c conda-forge cudatoolkit=11.8 cudnn=8.9.2

# Anything above 2.10 is not supported on the GPU on Windows Native
python -m pip install "tensorflow<2.11"

# Verify Tensorflow GPU installation:
python -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"

pip install Pillow scikit-learn numpy pandas matplotlib pandas seaborn missingno nltk graphviz pydot imutils notebook tensorflow-datasets==4.9.2
pip install --upgrade plotly
pip install --upgrade ipykernel ipyflow

ipython kernel install --user --name=dl_env
python -m ipykernel install --user --name dl_env --display-name dl_env

pip install notebook==6.1.5

conda install -y -c conda-forge jupyter_contrib_nbextensions jupyter_nbextensions_configurator
jupyter contrib nbextension install --user
jupyter nbextensions_configurator enable --user

jupyter nbextension enable scroll_down/main
jupyter nbextension enable autoscroll/main
jupyter nbextension enable execute_time/ExecuteTimes

pip install ultralytics

```

## Usage

```bash
jupyter notebook
```

then select TrashDetection&Classification notebook ใน folder src

## data preprocessing

ทำการโหลดข้อมูลโดย base จากชื่อ folder เป็น label

```bash

categories = ['battery', 'biological', 'brown-glass', 'cardboard', 'clothes', 'green-glass', 'metal', 'paper', 'plastic', 'shoes', 'trash', 'white-glass']

filenames_list = []
categories_list = []

for category in categories:
    filenames = os.listdir(base_path + category)
    
    filenames_list += filenames
    categories_list += [category] * len(filenames)

df = pd.DataFrame({
    'filename': filenames_list,
    'category': categories_list
})

df = add_class_name_prefix(df, 'filename')

df = df.sample(frac=1).reset_index(drop=True)
```
จากนั้นใช้ ImageGenerator สำหรับรูปภาพ


## TrashClassification model
 
ใช้ model YOLOV8 ในการทำ detection และจากรูปที่ได้ส่งเข้า model CNN MobileNetV2
รายละเอียดสามารถดูใน sandbox/trainModel.ipynb


## License

```bash
@software{yolov8_ultralytics,
  author = {Glenn Jocher and Ayush Chaurasia and Jing Qiu},
  title = {Ultralytics YOLOv8},
  version = {8.0.0},
  year = {2023},
  url = {https://github.com/ultralytics/ultralytics},
  orcid = {0000-0001-5950-6979, 0000-0002-7603-6750, 0000-0003-3783-7069},
  license = {AGPL-3.0}
}
``` 