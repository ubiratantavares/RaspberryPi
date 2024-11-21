# Instalação do Librosa no Raspberry Pi


This guide is designed to assist with the installation of Librosa on a 32-bit architecture Raspberry Pi (RPI). First, it’s necessary to determine the type of RPI you are using:

# Get information about RPI architecture  
uname -a

The output might vary depending on your RPI model. For example, for an RPI using armv7l architecture, the result could resemble:

Linux raspberrypi 5.10.103-v7l+ #1529 SMP Tue Mar 8 12:24:00 GMT 2022 armv7l GNU/Linux

This RPI architecture above might differ from your own, depending on your RPI type. As armv7l denotes a 32-bit architecture, installing Librosa directly on a 32-bit Raspberry Pi can be challenging. If you’ve spent significant time attempting installation, this guide aims to simplify the process.

For this tutorial, we’ll install Librosa Version 0.6.3 on Raspbian 5.10.103-v7l+, assuming the pip package manager with Python 3.7 is already installed. It’s advisable to create a virtual environment for Librosa and its dependencies:

To do that, you should run the script below since venv is built-in module in Python 3:

```bash
#create a virtual env  
python3 -m venv librosa_venv  
# activate a virtual env  
source librosa_venv/bin/activate
```

To install Librosa 0.6.3, we need to download and install the following dependencies:

- scipy v1.7.3
- llvm-7
- llvmlite v0.31.0
- numba v0.48.0
- numpy v1.21.4

# Scipy

Install Scipy using pip:

```bash
sudo pip3 install scipy==1.7.3
```


Since we are using an older version of llvm, it can be directly installed via `apt-get`, we'll install it using:

```bash
sudo apt-get install llvm
```

Once installation is completed, you can check the llvm version installed by the following command:

```bash
which llvm-config
```

For instance, the output might be “/usr/bin/llvm-config”.

Next, we install llvmlite 0.31.0 using the defined path to llvmlite config file (make sure you are using pip v3)

```bash
LLVM_CONFIG=/usr/bin/llvm-config pip3 install llvmlite==0.31.0
```


> Next, we install **compatible** numpy v1.21.4 and resampy v0.3.0 using PiWheels from — [https://www.piwheels.org/project/](https://www.piwheels.org/project/numpy/).

```bash
wget https://www.piwheels.org/simple/resampy/resampy-0.3.0-py3-none-any.whl#sha256=9cd5060d77328f23c733bc3db17724caa47d08f4b3b841244e85d7ba3f5661d9  
pip3 install resampy-0.3.0-py3-none-any.whl  
  
wget https://www.piwheels.org/simple/numpy/numpy-1.21.4-cp37-cp37m-linux_armv7l.whl#sha256=826319c22f05d7b50c3637af5563234edbb02f5634a08d314d21ef00271a32fe  
pip3 install numpy-1.21.4-cp37-cp37m-linux_armv7l.whl
```

We then have to install numba==0.48.0 librosa==0.6.3 using.

```bash
# specify a valid dependency tree with pi compatibility  
LLVM_CONFIG=/usr/bin/llvm-config pip3 install numba==0.48.0 librosa==0.6.3
```

# Testing

We can test the installation by writing a small Python script using the following command:

```bash
#run this on the shell  
nano testing.py
```

In the created file, type the information below

```bash
#write this after you nano into a shell  
import librosa
```

Lastly, run the testing script

```bash
#Type this to run the script   
python3 testing.py
```

If librosa is installed correctly, then it should not give any output in the terminal, indicating a perfect installation of librosa.

The following are links to reference articles and recommended solutions:

1. [https://medium.com/@sehgaladitya26/librosa-on-raspberry-pi-step-by-step-installation-guide-5b4f1bb536db](https://medium.com/@sehgaladitya26/librosa-on-raspberry-pi-step-by-step-installation-guide-5b4f1bb536db)
2. [https://stackoverflow.com/questions/63764962/install-librosa-on-raspberry-pi-4-error-with-the-wheel-of-llvmlite](https://stackoverflow.com/questions/63764962/install-librosa-on-raspberry-pi-4-error-with-the-wheel-of-llvmlite)
3. [https://www.piwheels.org/project/numpy/](https://www.piwheels.org/project/numpy/)
4. [https://www.piwheels.org/project/resampy/](https://www.piwheels.org/project/resampy/)
5. [https://www.youtube.com/watch?v=ye96YO-lz_4](https://www.youtube.com/watch?v=ye96YO-lz_4)
