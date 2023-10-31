把图像分为若干个互相没有重叠的window，在每个window内计算self-attention,
再通过shifted-window实现window间的交互，从而实现了全局建模。
在下图的4倍下采样和8倍下采样中，将特征图划分成了多个不相交的区域（Window）
并且Multi-Head Self-Attention只在每个Window内进行
Windows Multi-Head Self-Attention（W-MSA）模块和Shifted Windows Multi-Head Self-Attention（SW-MSA）模块是成对使用的，
假设第l层使用的是W-MSA，第l+1层就使用SW-MSA，通过窗口的移位使得第l层里不同的窗口进行信息交流。
为了解决移动前后窗口数不一致的问题，对窗口进行移位合并使其窗口数量与之前保持一致，并使用masked MSA，通过设置来隔绝不同区域的信息。
