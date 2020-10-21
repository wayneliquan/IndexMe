# Ubuntu 安装synergy源码

[toc]

## 安装步骤

- #### 安装依赖

  ```
  sudo apt install qtcreator qtbase5-dev qttools5-dev cmake make g++ xorg-dev libssl-dev libx11-dev libsodium-dev libgl1-mesa-glx libegl1-mesa libcurl4-openssl-dev libavahi-compat-libdnssd-dev qtdeclarative5-dev libqt5svg5-dev libsystemd-dev 
  ```

  

- #### 下载源码

- gitee： git clone https://gitee.com/mirrors/synergy-core.git

  或者 github： git clone https://github.com/symless/synergy-core.git

  推荐先用gitee下载，然后修改 .git/config 中的链接为github. 然后git fetch origin master.

- #### 编译

  ```
  cd synergy-core && mkdir build && cd build
  cmake ..
  make
  ```

  

- #### 创建启动脚本 synergy

  ```
  - cd /home/zlq/Source/synergy-core/build/bin
    nohup ./barrier >/dev/null 2>&1 &
  ```

  

## 参考地址

[2020-10-09 #「Synergy」- 编译安装（2.0.0）](https://www.cnblogs.com/k4nz/p/13784649.html)

https://github.com/symless/synergy-core/wiki/Compiling



