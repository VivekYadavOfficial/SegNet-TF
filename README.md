# SegNet-Tensorflow implementation
[October 09, 2018]  
I made minor bugfixes for toimcio/SegNet-tensorflow.   
https://github.com/toimcio/SegNet-tensorflow

# Usage
## 1. Training
```
$ cd ~
$ git clone https://github.com/PINTO0309/SegNet-TF.git

$ cd SegNet-TF
$ curl -sc /tmp/cookie "https://drive.google.com/uc?export=download&id=12wakrs1SSLTL50LuSibMTBpho_JySqFk" > /dev/null
$ CODE="$(awk '/_warning_/ {print $NF}' /tmp/cookie)"
$ curl -Lb /tmp/cookie "https://drive.google.com/uc?export=download&confirm=${CODE}&id=12wakrs1SSLTL50LuSibMTBpho_JySqFk" -o vgg16.npy

$ cd SegNet
$ curl -sc /tmp/cookie "https://drive.google.com/uc?export=download&id=1FgMelph4IQOrjs3b3TfuZE9uczo-Ex_6" > /dev/null
$ CODE="$(awk '/_warning_/ {print $NF}' /tmp/cookie)"
$ curl -Lb /tmp/cookie "https://drive.google.com/uc?export=download&confirm=${CODE}&id=1FgMelph4IQOrjs3b3TfuZE9uczo-Ex_6" -o CamVid.tar.gz
$ tar -zxvf CamVid.tar.gz
$ rm CamVid.tar.gz

$ curl -sc /tmp/cookie "https://drive.google.com/uc?export=download&id=1j16hiO2-9BRXKaVTGYKmrwQnN2yIkgw1" > /dev/null
$ CODE="$(awk '/_warning_/ {print $NF}' /tmp/cookie)"
$ curl -Lb /tmp/cookie "https://drive.google.com/uc?export=download&confirm=${CODE}&id=1j16hiO2-9BRXKaVTGYKmrwQnN2yIkgw1" -o sun3d_dataset.tar.gz
$ tar -zxvf sun3d_dataset.tar.gz
$ rm sun3d_dataset.tar.gz

$ sudo -H pip3 install tensorflow-gpu==1.11

$ cd ..
$ python3
>> from SegNet import SegNet
>> SegNet().train()
```
## 2. Slimming weight files for deployment
A weight file after slimming is generated under the "ckpt" folder.
```
$ python3 SegNetInfer.py
```
## 3. Freeze graph
```
$ python3 freeze_graph.py \
--input_graph=ckpt/deployfinal.pbtxt \
--input_checkpoint=ckpt/deployfinal.ckpt \
--output_graph=ckpt/deployfinal.pb \
--output_node_names=conv_classifier/output \
--input_binary=False
```

# Environment
Requirement: Tensorflow-GPU 1.11.0  
Ubuntu: 16.04  
python: 3.5.2  
CUDA: 9.0  
cuDNN: 7  
GPU:Geforce GTX 1070  









