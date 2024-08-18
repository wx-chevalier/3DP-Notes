# 树脂 3D 打印中的抗锯齿 (AA) 和模糊

几种 3D 打印技术，例如 [SLA、MSLA 和 DLP](https://www.liqcreate.com/zh-CN/支持文章/sla-dlp和lcd-3d打印机有什么区别/) 用于逐层固化感光树脂，形成 3D 打印物体。为了获得 3D 打印部件，DLP 打印机使用 [DMD 芯片](https://www.liqcreate.com/zh-CN/支持文章/解释了-2k-4k-8k-分辨率-3d-打印机和树脂/) 以暴露每一层中的正确像素。在 MSLA 3D 打印机中，这是通过 LCD 屏幕完成的。两个图像都是由像素组成的。每个像素都可以单独打开或关闭。在打开的像素处，光源将暴露树脂，使其局部固化。关闭的像素会阻挡光线，树脂不会固化。因此，当近距离观察表面时，完美的印刷品将始终具有像素化表面。可以使用抗锯齿 (AA) 和模糊等新的曝光技术来减少像素化。但是，如果使用不当，会降低尺寸精度或产生不良的表面光洁度。

![img](https://assets.ng-tech.icu/item/sla-dlp-lfs-04_1.jpg__1184x0_q85_subsampling-2.jpg)_来自 formlabs 的图片：DLP 投影仪中的像素与其激光技术相比。一个_ _DLP 使用数字投影仪在整个平台上一次投影每一层的单个图像。由于每一层的图像都是数字显示的，所以它是由许多正方形像素组成的。_

## 什么是抗锯齿 (AA) 和模糊？

网上有很多信息，例如软件开发人员 [奇图盒](https://www.chitubox.com/en/article/support/indepth/technology/52). 由于并非所有信息都清楚，我们决定执行我们自己的测试并将结果发布在本文中。很多理论都是基于 Autodesk Ember 团队进行的研究。他们研究了如何制作单个体素以及灰度如何工作。他们将像素从深灰色（几乎是纯黑色）排列到纯白色以固化树脂。他们的研究表明，当灰度级低于某个值时，不会有反应（固化）。但是，从深灰色到一定的临界亮度，树脂中开始形成半圆形的固化部分。在实践中，灰色像素（半圆形固化体素）将合并到相邻（完全固化）体素中。通过控制像素的亮度，可以产生任意大小的体素，并且可以达到亚像素精度（理论上）。在下面的视频中了解有关 Autodesk 测试和理论的更多信息。

像 EnvisionTEC / ETEC 等具有封闭 DLP 系统的公司一直在使用此系统和类似系统 [像素操作](https://patents.google.com/patent/EP1894705B1/en) 工具很长一段时间来实现更高分辨率的打印。直到最近它才被集成到开放式树脂 3D 打印机中，值得在切片机中输入随机值之前阅读结果。

## 抗锯齿 (AA) 和模糊的测试设置 Liqcreate 树脂。

对于这个测试，我们选择了一个完全开放的树脂 3D 打印机，[Elegoo Mars 3](https://www.elegoo.com/collections/3d-printing?gclid=CjwKCAiAvaGRBhBlEiwAiY-yMKeegCmlIBXUK3Ww8bfkj8clZlDtb3clYstNJ7AFkNiSMPbLGYH_CBoCls8QAvD_BwE) 与...结合 [Liqcreate Clear Impact](https://www.liqcreate.com/zh-CN/ 产品展示/clear-impact/). 每次测试都使用 50 微米设置 [设置数据库](https://www.liqcreate.com/zh-CN/支持文章/3D打印参数-elegoo-mars-3/). Chitubox 软件（免费版）和 Elegoo Mars 3 固件更新到最新版本（Chitubox V1.9.1 和 Mars 3 [firmware V4.5.0-1.0-e13_LCDE1_4098X2560_F21.28](https://www.elegoo.com/blogs/3d-printing/mars-3-3d-printer-support-files)）。Chitubox 有两个设置可以设置为 Mars 3. 首先是抗锯齿 (AA)，可以关闭，或设置为灰度 0 到 8 之间的数字。此外，可以关闭模糊的级别，或设置在因子 2 或 4 之间。

## 抗锯齿和模糊如何用于树脂 3D 打印？

像素化表面在打印部件的弯曲区域最为明显。我们在这个测试中使用了一个 50 毫米高的半球体。在本文后面显示切片图像时，它始终位于零件弯曲区域的球体的一半。

_![img](https://assets.ng-tech.icu/item/AA-layer-500.png)_

_图像：半球体和半球体的横截面。_

让我们看看使用抗锯齿 (AA) 和模糊设置在 Chitubox 中生成什么样的图像。关闭 AA 和模糊时的原始切片图像如下所示。纯黑白像素。

![img](https://assets.ng-tech.icu/item/No-AA.png)

_图像：关闭 AA 和模糊时的纯黑白像素。_

当关闭 AA 和 Blur 时，球形看起来会像下图那样像素化。

_![img](https://assets.ng-tech.icu/item/AA-max.png)_

_图像：切片器将计算每一层的像素，结果是一个像素化的表面，尤其是对于球形形状可见。_

这个像素化的表面可以通过抗锯齿（灰度）和模糊设置进行操作，如果使用得当的话。在下图中，您可以看到选择抗锯齿选项时灰度的作用。G0 表示灰度级 0（这是最低灰度级），数字越大表示灰度级越高。在图像中，可以看到外边缘获得了额外的灰色像素层。在灰度 2 之前，灰度的数量会增加，而从灰度 3 起，只有像素的强度更亮。在灰度 8 下，所有像素又是黑白的，这完全没用。在所有情况下，模糊功能都已关闭。

![灰色和模糊灰度像素树脂 3D 打印 Elegoo Mars Saturn 抗锯齿 抗锯齿 抗锯齿 AA](https://assets.ng-tech.icu/item/Grey0B0-tm-G8B0.png)

让我们看看模糊功能是如何工作的。在此示例中，在灰度 0 上启用了抗锯齿 (AA) 选项，并且模糊功能从左侧的 Blur off 更改为右侧的 Blur 4。

![img](https://assets.ng-tech.icu/item/Left-to-right-Grey0-blur-uit-G0B2-G0B3-G0B4.png)

_图像：切片文件的示例是在灰度级别 0 上启用了抗锯齿 (AA) 选项。模糊级别从左侧的模糊关闭变为右侧的模糊 4。_

正如在前面的测试中看到的，灰度函数将只操纵外部像素的灰度。模糊功能将控制有多少外层会受到灰度的影响。需要注意的是，在高度模糊的情况下，灰度同时开始向内渲染，导致中心区域的原始白色像素变为灰色。这可能会导致光功率不足，并可能导致固化问题。选择图像模糊级别时，请注意选择较高级别。

## 打印机如何响应抗锯齿和模糊？

很高兴看到 Chitubox 切片器在抗锯齿和模糊方面工作得非常好，但硬件也能正常工作也很重要。在一个 [从 2021 年 XNUMX 月开始学习](https://www.reddit.com/r/AnycubicPhoton/comments/lcpfxk/anycubic_photon_mono_antialiasing/)，一个 Anycubic Photon Mono 用户在他们的打印机上尝试了抗锯齿，发现特定的打印机没有按预期工作。打印机不是灰度级，而是将灰度级解释为 100% 亮度下的较短曝光时间。虽然它应该是在较低亮度下的 100% 曝光时间。

随着 [来自 Github 的 UV 工具](https://www.liqcreate.com/zh-CN/支持文章/解释了在树脂-3D-打印中测试的抗锯齿-aa-和模糊/Release-v2.29.0-·-sn4k3/UVtools-·-GitHub)，我们设计了一个不同灰度等级的文件来测试是否更新了 Elegoo Mars 3 会妥善处理。

_![img](https://assets.ng-tech.icu/item/Grayscale-test2.jpg)_

_图像：具有不同灰度/亮度级别的设计文件_

_![灰色和模糊灰度像素树脂 3D 打印 Elegoo Mars Saturn 抗锯齿 抗锯齿 抗锯齿 AA](https://assets.ng-tech.icu/item/Grayscale-test-scaled.jpg)_

_图片： Elegoo Mars 3 启用抗锯齿 (AA) 或灰度级时，一次曝光 3 个不同的亮度级别。_

从上面的图像和测试可以看出，灰度在最新版本的 Elegoo Mars 3 与 Chitubox 结合使用。下一步是查看实际结果。

## 树脂 3D 打印在实践中的抗锯齿

本文测试了 18 种不同的配置，总打印时间超过 144 小时。我们从参考开始，使用各种不同的 AA 和模糊设置以 50 微米的层厚对半球体进行切片。关闭抗锯齿功能后，可以看到像素化表面。

_![img](https://assets.ng-tech.icu/item/No-AA-pixels-vs-printed-part.png)_

_图像：抗锯齿关闭，结果是像素化表面（AA=关闭；B=关闭）。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![img](https://assets.ng-tech.icu/item/G0B0.png)_

_图像：抗锯齿在 0 级打开，模糊关闭 (AA0;B0)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![灰色和模糊灰度像素树脂 3D 打印 Elegoo Mars Saturn 抗锯齿 抗锯齿 抗锯齿 AA](https://assets.ng-tech.icu/item/G1B0.png)_

_图像：抗锯齿在 1 级打开，模糊关闭 (AA1;B0)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![img](https://assets.ng-tech.icu/item/G2B0.png)_

_图像：抗锯齿在 2 级打开，模糊关闭 (AA2;B0)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![img](https://assets.ng-tech.icu/item/G3B0.png)_

_图像：抗锯齿在 3 级打开，模糊关闭 (AA3;B0)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![灰色和模糊灰度像素树脂 3D 打印 Elegoo Mars Saturn 抗锯齿 抗锯齿 抗锯齿 AA](https://assets.ng-tech.icu/item/G4B0.png)_

_图像：抗锯齿在 4 级打开，模糊关闭 (AA4;B0)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![灰色和模糊灰度像素树脂 3D 打印 Elegoo Mars Saturn 抗锯齿 抗锯齿 抗锯齿 AA](https://assets.ng-tech.icu/item/G5B0.png)_

_图像：抗锯齿在 5 级打开，模糊关闭 (AA5;B0)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![灰色和模糊灰度像素树脂 3D 打印 Elegoo Mars Saturn 抗锯齿 抗锯齿 抗锯齿 AA](https://assets.ng-tech.icu/item/G6B0.png)_

_图像：抗锯齿在 6 级打开，模糊关闭 (AA6;B0)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![灰色和模糊灰度像素树脂 3D 打印 Elegoo Mars Saturn 抗锯齿 抗锯齿 抗锯齿 AA](https://assets.ng-tech.icu/item/G7B0.png)_

_图像：抗锯齿在 7 级打开，模糊关闭 (AA7;B0)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![img](https://assets.ng-tech.icu/item/G8B0.png)_

_图片：抗锯齿在 max 级别（级别 8）和模糊关闭（AA8；B0）。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

## 关于抗锯齿（灰度）的结论

不幸的是，很难在图片中捕捉像素并在相似条件下比较所有部分。当查看彼此相邻的部件时，在启用抗锯齿并关闭模糊时，所有部件的表面上都有可见的像素。查看部件上侧的像素，抗锯齿级别 2 和 3 表现最佳，抗锯齿级别 7、8 和关闭时表现最差。让我们看看如果我们将它与模糊结合会发生什么。

## 在实践中使用树脂 3D 打印进行模糊处理

在抗锯齿（或灰度）旁边，大多数基于树脂的 3D 打印机都提供模糊选项。抗锯齿会影响对象周围的外部像素层，并创建不同级别的灰度像素。Blur 功能将与 Anti-Aliasing 一起使用，并将影响多少外部像素获得灰度。在这个测试中，模糊级别 2 是在不同级别的抗锯齿之上测试的。模糊级别 2 是撰写本文时可用的最低模糊级别。更高的级别也倾向于向内渲染并且未经测试。

_![灰色和模糊灰度像素树脂 3D 打印 Elegoo Mars Saturn 抗锯齿 抗锯齿 抗锯齿 AA](https://assets.ng-tech.icu/item/G0B2.jpg)_

_图片_: _在最低级别（级别 0）进行抗锯齿，在级别 2 进行模糊处理（AA0；B2）。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![img](https://assets.ng-tech.icu/item/G1B2.png)_

_图片_: _级别 1 的抗锯齿和级别 2 的模糊 (AA1;B2)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![img](https://assets.ng-tech.icu/item/G2B2-pixels-vs-printed-part.png)_

_图片_: _级别 2 的抗锯齿和级别 2 的模糊 (AA2;B2)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![灰色和模糊灰度像素树脂 3D 打印 Elegoo Mars Saturn 抗锯齿 抗锯齿 抗锯齿 AA](https://assets.ng-tech.icu/item/G3B2.png)_

_图片_: _级别 3 的抗锯齿和级别 2 的模糊 (AA3;B2)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

_![灰色和模糊灰度像素树脂 3D 打印 Elegoo Mars Saturn 抗锯齿 抗锯齿 抗锯齿 AA](https://assets.ng-tech.icu/item/G4B2.png)_

_图片_: _级别 4 的抗锯齿和级别 2 的模糊 (AA4;B2)。左边是 3D 打印的零件，右边是零件中间的切片层的横截面。_

## 关于抗锯齿 (AA) 和模糊的结论

AA 和 Blur 有助于减少树脂 3D 打印部件的像素化。应根据树脂和应用研究最佳设置是什么。通过切换抗锯齿 (AA) 并关闭模糊可以获得最佳精度，但是当树脂正确拨入时，像素将可见。

如果需要减少像素化，最好将灰度级保持在 0 到 4 之间，或者关闭模糊，或者使用 max 最多 2 级模糊。使用抗锯齿和模糊时，表面将具有较少定义的像素，并且可能会出现一些其他小的缺陷，例如模糊表面的条纹。

查看我们的结果，我们是否使用过 [Liqcreate Clear Impact](https://www.liqcreate.com/zh-CN/ 产品展示/clear-impact/) 树脂上 Elegoo Mars 3 和 Chitubox 作为切片机。我们发现最好的结果是抗锯齿（灰度）级别为 3 与模糊级别 2 相结合。一些较小的细节（在像素级别）与像素一起被冲掉。如果这对您的应用程序来说是可以接受的，那么可以选择使用抗锯齿和模糊设置。
