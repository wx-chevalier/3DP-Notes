# DLP 工艺

在大多数情况下，DLP 比 SLA 更快。 与激光必须接触每一个点的 SLA 打印机相比，DLP 打印机将一次性曝光完整的构建板。 根据 SLA 打印机制造商 Formlabs: “根据经验，这使得 SLA 3D 打印机在打印中小型单个零件时具有可比性或速度更快，而 DLP 3D 打印机可以更快地打印大型、完全密集的打印件，或者使用填充很多的多个零件构建平台的。”

除了速度之外，还有两个明显的区别。 一个是激光是一个圆点，当它围绕它移动时，它是一条带有圆边的线。 根据激光光斑的大小，它可以打印非常准确。 但是，激光光斑越小，打印机的速度就越慢。 而 DLP 依赖于像素化图像。 使零件的边缘也像素化。

![SLA、DLP 和 LFS（低力立体光固化成型）之间的区别](https://formlabs.com/_next/image/?url=https%3A%2F%2Fformlabs-media.formlabs.com%2Ffiler_public_thumbnails%2Ffiler_public%2F0a%2F6b%2F0a6b7fb3-8e08-4ebc-a397-f91399779545%2Fsla-dlp-lfs-04_1.jpg__1354x0_q85_subsampling-2.jpg&w=1920&q=75)

借助许多软件技巧，例如 AA（抗锯齿）、模糊和像素偏移，可以将 DLP 打印机的这些外部像素处理成平滑的图像。 在极端成像中，它可能如下图所示。

![模型有机形状上 XY 体素的差异](https://formlabs.com/_next/image/?url=https%3A%2F%2Fformlabs-media.formlabs.com%2Ffiler_public_thumbnails%2Ffiler_public%2F9b%2Fea%2F9bea1736-0643-4f1f-9969-353fbd61dd49%2Fsla-v-dlp_hero-3png__1354x0_q85_subsampling-2.png__1354x0_q85_subsampling-2.png&w=1200&q=75)
