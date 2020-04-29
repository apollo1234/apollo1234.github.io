## Windowns 平台下 print 乱码
Windows 平台 python 默认编码不是 utf-8，需要改变下编码：

···
import io
import sys
import urllib.request
sys.stdout = io.TextIOWrapper(sys.stdout.buffer,encoding='utf8') #改变标准输出的默认编码
···
