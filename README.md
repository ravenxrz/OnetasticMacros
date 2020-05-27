# OnetasticMacros
本项目用于收藏个人常用的Onetastic宏，下面只提及[macroland](https://getonetastic.com/macroland)中无法下载的宏。

## 目录（pandoc导出版).xml

这个宏用于实现在OneNote中自动生成文本目录导航，文本是必须通过typora（pandoc）导出的文本（即markdown转docx的文本）。这样说可能不太好理解，直接看下面的视频：https://www.bilibili.com/video/BV1uZ4y1W7Xf

这里说一下**原理**，避免出现无法生成目录的“bug”：

既然避免了用户手动添加各级标题样式， **那自然需要另一种方式来识别要被添加到目录的标题。** 根据个人的观察，在typora中导出H1,H2,H3,H4,H5的特征如下：

1. 所有标题颜色均为 **#4F81BD**
2. H1 字体大小为16，加粗
3. H2字体大小为14，加粗
4. H3字体大小为12，加粗
5. H4字体大小为12，斜体
6. H5字体大小为12，normal

所以在实现这个宏时，首先过滤出所有颜色为 **#4F81BD** 的文本，再根据字体大小和是否加粗/斜体来找到标题文本，最后生成相应的超链接即可。

也就是说，想要自动生成目录，就不要去修改这些样式。

额外说明：

1. typora导出docx是基于pandoc导出的，所以本方案兼容pandoc命令

2. 本宏改自：https://getonetastic.com/macro-01C7C254D45E462CB24B3246853B3032
