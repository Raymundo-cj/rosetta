## Linux下安装rosetta步骤

### 第一步：安装cmake软件

在下面的网站中下载cmake软件（因为自己是全新的服务器，所以什么软件都没有），如果已经有这个软件，可以跳过。
`https://cmake.org/files/`
建议安装比较新的版本，我这里下载的是`https://cmake.org/files/v3.27/cmake-3.27.0-rc3-linux-x86_64.tar.gz`

#### 安装按照下面的顺序执行代码：
```
wget https://cmake.org/files/v3.27/cmake-3.27.0-rc3-linux-x86_64.tar.gz #这步服务器太慢可以在电脑上下载好直接上传

tar xvf cmake-3.27.0-linux-x86_64.tar.gz
```
#### 设置环境变量
```
vim /etc/profile

export CMAKE_HOME=/home/ubuntu/soft/cmake/cmake-3.27.0-rc3-linux-x86_64/bin

export PATH=$CMAKE_HOME:$PATH

source /etc/profile
```
#### 检查安装是否成功
```
cmake -version
```
### 第二步：安装rosetta软件

#### 下载rosetta软件安装包
`https://manual.gromacs.org/documentation/current/download.html`我在采用的方法是
```
wget ftp://ftp.gromacs.org/gromacs/gromacs-2023.1.tar.gz
```

#### 解压及后续安装

```
tar xfz gromacs-2023.1.tar.gz
cd gromacs-2023.1
mkdir build
cd build
cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON
make
make check # 这个执行完会有一些报错信息，接着往下执行也可以安装成功，不是很懂为啥？
sudo make install
source /usr/local/gromacs/bin/GMXRC
```












