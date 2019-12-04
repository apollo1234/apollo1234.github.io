## apk 瘦身指南

- 包体积和转换率
   - 一个 APK 的大小每增长 6 MB，下载转化率就有 1% 的降低。
   - 一个 10MB 的 app 的下载完成率将比 100MB 的 app 高大约 30%。

---

- 整体优化
    - 插件化
    - 7zip 压缩 .arsc，爱奇艺少了 2M 多
    - apksigner 替换 jarsigner，体积减少 5%
        - jarsigner是针对每个文件进行了签名，然后针对签名后的文件计算摘要，并写入到META-INF文件夹下的MANIFEST.MF文件里面；而apksigner直接计算所有文件的摘要，写入MANIFEST.MF文件。
- 资源优化
    - 一套资源（xhdpi）
        - 一套资源，低密度手机会缩放图片，高密度手机会拉伸图片。
    - 重复资源 
        - MD5 找出名字不同，资源相同的图片
    - lint 检查无用的资源 
    - gradle 移除无用的资源
        - 打开shrinkResources也必须打开minifyEnabled
    - png 图片压缩
        - pngcrush,pngquant,zopflipng
        - www.tinypng.com
    - 转 webp 格式
        - 有损WebP是基于VP8视频编码中的预测编码方法来压缩图像数据；
        - 无损WebP基于使用不同的技术对图像数据进行转换；
        - 有损WebP(支持透明度)区别于有损WebP和无损WebP，这种编码允许对RGB频道的有损编码同时可对透明度频道进行无损编码。
        - 有些图片压缩后反而会增大。WebP对色差比较小的图片，压缩比会比较高
    - 大背景图
        - 后台下载
    - 动画 优化
        - Lottie
- 代码优化
    - 代码混淆
        - minifyEnabled
    - 无用代码扫描
        - https://github.com/SonarSource/sonarqube
    - 删除 R 文件，直接引用常量
        - https://github.com/meili/ThinRPlugin/blob/master/README.zh-cn.md
    - 注解代替枚举
        - Google 强烈推荐，减少体积和节省内存
- asrc 优化
    - resConfigs
- lib 目录优化
    - 对 arm 提供支持，
    
---
### 参考：
- [爱奇艺Android移动客户端app瘦身经验](https://mp.weixin.qq.com/s/xVCJ-MMt1KSO7kpN4CFXBQ)
- [缩小APK，增加下载量](https://juejin.im/post/5a388c73518825696f7e1ddb)
