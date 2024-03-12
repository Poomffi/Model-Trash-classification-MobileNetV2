# Trash Classification

Trash classification is the process of sorting waste materials into distinct categories.

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

then select TrashClassification notebook


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