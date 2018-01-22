## OpenCV 的基本数据类型

OpenCV 提供了多种基本数据类型的定义，但是由于 Python 是一门弱类型语言，OpenCV 在 Python 中的 API 接口提供的数据类型大多直接使用 Python 原生的原子类型或借用 Python 中 NumPy 模块中的数据类型，下面介绍几个基本的数据类型。

首先是最简单的数据类型 CvPoint。CvPoint 是一个包含 int 类型成员 x 和 y 的简单结构体。它还有其他变体形式，比如 CvPoint2D32f,CvPoint3D64f 等等。前者同样由两个成员 x,y，但他们是浮点类型；而后者却多了一个浮点类型的成员 z 。这个结构体定义了在二维或者三维空间中的一个点，在 Python 中使用一个 2 个变量或者 3 个变量的 tuple(x, y) 来表示。

CvSize 类型与 CvPoint 非常相似，但它的数据成员是 int 类型的 width 和 height。如果希望使用浮点类型，则选用 CvSize 的变体类型：CvSize2D32f。在 Python 中 同样使用 tuple(width, height) 来表示
