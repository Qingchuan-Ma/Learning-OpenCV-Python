## 下载和安装 OpenCV

本书采用 OpenCV-Python 接口，因此下载和安装相对简单。本书的所有程序运行环境都为 Anaconda 下，并在此环境下安装 OpenCV。

### Anaconda


#### 什么是 Anaconda

Anaconda 是一个开源的 Python 发行版本，其包含了 conda, Python 等180多个科学包及其依赖项。Anaconda 是目前最流行的 Python 数据科学平台。

#### 为什么选择 Anaconda

1. 创新：有获取最新的数据科学创新和通过创新的开源分析从数据中提取价值的能力
2. 效率：是一个具有可伸缩协作、部署、快速原型和端到端数据科学工作流的企业平台
3. 安全：是一个受信任和管理的数据科学分布，有身份管理以及安全管理你的开源生态系统的能力
4. 社交：一个专家社区，包括开源开发者、数据科学家、业务分析师、数据工程师、DevOps 和数据科学以及 IT 管理人员。

#### 下载和安装

前往该网站 https://www.anaconda.com/download/ 下载对应系统的发行版。如果有能力也可以下载企业版。目前 Anaconda 支持 Windows, Linux, MacOS 三个操作系统。并且支持的 Python 也有 3.6 与 2.7 版本。本书采用 Python 3.6 版本。下载后点击安装即可。

### OpenCV3

Anaconda 使用的包管理工具为 conda，因此使用 conda 命令进行安装即可。打开命令行或者终端，输入下面代码：
```shell
$ conda install --channel https://conda.anaconda.org/menpo opencv3
```
安装成功后，可以使用 Anaconda 中名为 Spyder 的 IDE，并在 Console 中输入下面代码进行测试：
```python
import cv2
print cv2.__version__
```
如果输出版本号，则说明安装成功。
