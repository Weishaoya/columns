对 detr 进行改进，用 deformable attention 代替 attention

变体：采用二阶段，第一阶段得到 proposal ，第二节阶段精调 bounding box。具体来说，第一阶段将 Encoder 的输出直接通过一个简单的检测头（FFN+二分类线性层）得到前景和背景的 bounding box，对这些 bounding box 按照分数排序并取 top k，将 top k 作为第二阶段 decoder 的 queries ；第二阶段的 decoder 有多层，每一层将前一层输出的 bbx 作为 queries 输入，得到精调后的 bbx 输出，不同解码层的预测头不共享参数。
