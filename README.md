# tensorflow1.6-CUDA9.0-cuDnn7.0-Installation

I spend half a day to install tensorflow1.6-cuda9.0-cuDnn7.0 on Win10. Just write it down in case others or myself need it in future.

The following are steps:

1) install Python3.5 for win10
2) install PyCharm Commnunity Edition compliling Python for win10
3) open the PyCharm Settings (see PyCharm Settings.png image), we choose the Python3.5 as the interpreter, by clicking the + button, we install tensorflow1.6.0-gpu and other related packages we need such as pandas, numpy...

4) download cuda_9.0 for win10 for NVDIA official website and install it following instructions (by default: it will be installed at following location: C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0) -- in this step, if your hardware does not support cuda_9.0, it will report errors to you.

5) download cudnn-9.0-windowns10-x64-v7. this file only includes some library files: bin/cudnn64_7.dll, include/cudnn.h, lib/x64/cudnn.lib. so we do not need to install anything. Note that here we only need to

     --- copy cudnn64_7.dll to: 'C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\bin'

     --- copy cudnn.h to: 'C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\include'

     --- copy cudnn.lib to: 'C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\lib\x64'

6) configure environmental variables
    
    --- open Control Panel - System and Security - System - Advanced system settings - Environmental Variables (see the EV.png picture)
    
    --- click the path - edit - add following path to path variale (see the path.png picture)
        
          C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\cuda
          
          C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\lib\x64
          
          C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\extras\CUPTI\libx64
          
          C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\bin
          
          C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\include
          
  7) write the following code in Pycharm:
 
     import tensorflow as tf

     sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))
     
     we should get something like below (without reported errors):
     
     2018-03-15 09:45:07.000249: I C:\tf_jenkins\workspace\rel-win\M\windows-gpu\PY\35\tensorflow\core\platform\cpu_feature_guard.cc:140]      Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2
     ...
 
 Notes: I only tried tensorflow1.6.0+cuda9.0+cudnnV7.0. Looks like that these selected versions should be matched with each other. 

The simple way to run tensorboard from pycharm is as follows:

1) In pycharm terminal windown, change directory to (the directory of your tensorboard): 

cd C:\Users\xuh3\AppData\Roaming\Python\Python35\site-packages\tensorboard

2) run the below command:

python main.py --logdir Y:\skin_image_seg\tmp\retrain_logs\train

or try this: tensorboard --logdir=path\to\log-directory

(go to your project directary, i.e., in our deep learning machine)

or in my pycharm win10, I use: python -m tensorboard.main --logdir=./tmp/autoencoder
(./tmp/autoencoder   # is my directory for saving my history file)

3) open the following provided link for tensorboard visulation (example see tensorboard.png)

TensorBoard 1.5.1 at http://LRI-107580:6006 (Press CTRL+C to quit)

