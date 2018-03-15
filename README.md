_7# tensorflow1.6-CUDA9.0-cuDnn7.0-Installation

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
