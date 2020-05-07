---
layout: post
title: Anaconda使用整理
---



Anaconda是一個用於科學計算的Python發行版，支持 Linux, Mac, Windows系統，提供了包管理與環境管理的功能，可以很方便地解決多版本python並存、切換以及各種第三方包安裝問題。 Anaconda利用工具/命令conda來進行package和environment的管理，並且已經包含了Python和相關的配套工具。

<!-- more -->

## Conda的環境管理

Conda的環境管理功能允許我們同時安裝若干不同版本的Python，並能自由切換。對於上述安裝過程，假設我們採用的是Python 2.7對應的安裝包，那麼Python 2.7就是默認的環境。

假設我們需要安裝Python 3.4，此時，我們需要做的操作如下：

```bash
#創造一個名為python34的環境，版本為Python3.4
conda create --name python34 python=3.4

activate python34 # for Windows
source activate python34 # for Linux & Mac

#此時輸入
python --version
# 可以得到`Python 3.4.5 :: Anaconda 4.1.1 (64-bit)`

#返回至默認環境運行
deactivate python34 # for Windows
source deactivate python34 # for Linux & Mac

#刪除現有的環境
conda remove --name python34 --all
```

用戶安裝的不同python環境都會被放在目錄~/anaconda/envs下，可以在命令中運行conda info -e查看已安裝的環境，當前被激活的環境會顯示有一個星號或者括號。



## Conda's Package management

Conda的包管理就比較好理解了，這部分功能與pip類似。

例如，如果需要安裝scipy：

```bash
# 安装scipy
conda install scipy

#查看已經安裝的packages
conda list
```

conda的常用操作如下:

```bash
#查看已經安裝的packages
conda list

#查看特定環境已安裝的包
conda list -n python34

#查詢package訊息
conda search numpy

# 安裝package
conda install -n python34 numpy
# 如果不用-n指定環境名稱，則被安裝在當前活躍環境
# 也可以通過-c指定通過某個channel安裝

#更新package
conda update -n python34 numpy

# 删除package
conda remove -n python34 numpy
```