# 载入图像

为了在窗口中显示图像，我们需要了解如何从磁盘中载入图像。OpenCV 为我们提供了 cv.imread()，如下所示：
```python
cv2.imread(filename[, flags]) -> retval
```
当打开一副图像时，cv2.imread() 并不分析文件扩展名，而是通过分析图像文件的前几个字节来确定图像的编码格式。第二个参数 flags 有几个值可以选择。默认情况下，图像是以每个通道 8 位，3 个通道的形式被读入。下面是几个重要的可设参数：
1. cv2.IMREAD_ANYDEPTH: 设置以后可读入非 8 位的图像，否则转换成 8 位
2. cv2.IMREAD_COLOR: 设置以后始终将原图转换成彩色图像
3. cv2.IMREAD_GRAYSCALE: 设置以后始终将原图转换成灰度图
4. \> 0: 返回 3 通道彩色图像
5. = 0: 返回灰度图
6. < 0: 按原图返回（可以含有 alpha 通道）

需要注意的是，当 cv2.imread() 读入失败，并不会产生一个运行时错误，而是返回一个空指针。

与 cv2.imread() 对应的函数是 cv2.imwrite()，实现了保存图像功能， cv2.imwrite() 有两个参数：
```python
cv2.imwrite(filename, img[, params]) -> retval
```
第一个参数表示文件名，其中后缀部分用来制定图像存储的编码格式。第二个参数指向要存储的图像数据。回忆前一章讲到的，img 是一个 python 中 NumPy 模块的 array 数组，可以由 cv2.imread() 函数获得，也可以自己创建。第三个参数可以有以下选择：
1. 对于 JPEG 格式，该参数为 ( CV_IMWRITE_JPEG_QUALITY )，值从 0 到 100，默认为 95
2. 对于 WEBP 格式，该参数为 ( CV_IMWRITE_WEBP_QUALITY )，值从 1 到 100，默认为 100
3. 对于 PNG 格式，该参数为 ( CV_IMWRITE_PNG_COMPRESSION )，值从 0 到 9，值越高意味着更小的文件大小和更长的压缩时间，默认为 3
4. 对于 PPM, PGM 或者 PBM 格式，该参数为 ( CV_IMWRITE_PXM_BINARY )，值为 0 或 1，默认为 1

需要注意的是，只有8位（或16位无符号如 PNG, JPEG 2000 和 TIFF）单通道或 3 通道（使用BGR通道顺序）图像可以使用此函数保存。如果格式、深度或者通道顺序不同，先使用 cv2.cvtColor() 转换成可保存的图像数据。

还可以使用这个函数将图像存储为含 alpha 通道的 PNG 图像中。要做到这一点，创建 8位（或 16 位）4 通道图像 BGRA，alpha 通道在最后。完全透明的像素应该让 alpha 值设置为 0，不透明的像素应该设置为 255/65535。当存储成功是，返回 1，否则返回 0。
