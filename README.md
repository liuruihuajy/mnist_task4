# 基于三层神经网络的MNIST图像分类的实验报告
## 1. 模型介绍
本实验采用三层神经网络（一个输入层、一个隐藏层和一个输出层）作为分类器，对MNIST手写数字数据集进行分类。模型允许自定义隐藏层的大小和激活函数类型，支持通过反向传播算法计算给定损失的梯度，进而更新模型参数。本实验中，激活函数采用了常用的ReLU函数，并在输出层使用Softmax函数进行多分类。
- 模型权值：https://github.com/liuruihuajy/mnist_task4/blob/main/MNIST.pt

## 2. 数据集介绍
MNIST是一个包含70,000个手写数字图像的数据集，其中60,000个用于训练，10,000个用于测试。每个图像都是28x28的灰度图，数字范围是0到9。由于其规模的适中以及任务的典型性，MNIST已成为计算机视觉和深度学习领域的一个基准数据集。
- 数据集链接：http://yann.lecun.com/exdb/mnist/
## 3. 实验设置
### 3.1 模型参数
隐藏层大小：实验中尝试了不同大小的隐藏层，如64、128、256个神经元。</br>
激活函数：ReLU（Rectified Linear Unit）</br>
输出层：Softmax函数用于多分类</br>
损失函数：交叉熵损失（Cross-Entropy Loss）</br>
正则化：L2正则化用于防止过拟合</br>
### 3.2 训练参数
学习率：初始学习率设为0.01，并使用了学习率下降策略，如每过一定轮数将学习率乘以一个衰减因子。</br>
批量大小：设为64</br>
迭代轮数：根据验证集性能确定最佳迭代轮数，这里设置为50</br>
优化器：随机梯度下降（SGD）</br>
### 3.3 超参数查找
通过网格搜索或随机搜索等方法，调节学习率、隐藏层大小、正则化强度等超参数，观察并记录模型在不同超参数下的性能。</br>
## 4. 模型训练过程可视化
在训练过程中，我们记录了训练集和验证集的损失以及准确率随迭代轮数的变化。通过绘制这些曲线，可以直观地观察到模型的训练过程，包括是否出现过拟合、学习率是否合适等信息。此外，我们还记录了最优模型权重对应的超参数设置。

## 5. 实验结果
### 5.1 超参数对性能的影响
通过实验发现，隐藏层大小对模型性能有较大影响。随着隐藏层大小的增加，模型的容量增加，能够学习到更复杂的特征，从而提高分类准确率。但是，当隐藏层过大时，模型容易出现过拟合现象，导致在验证集上的性能下降。因此，需要选择一个合适的隐藏层大小。
学习率也是一个重要的超参数。较大的学习率可以加速训练过程，但可能导致模型在最优解附近震荡而无法收敛；较小的学习率虽然能够保证模型的收敛性，但训练过程会变得非常缓慢。因此，需要根据实际情况选择合适的学习率，并可能采用学习率下降策略来进一步提高模型的性能。
正则化强度对防止过拟合也有重要作用。适当增加正则化强度可以提高模型在验证集上的性能，但过强的正则化可能导致模型无法学习到有效的特征表示。
### 5.2 最终模型性能
经过超参数查找和模型训练，我们得到了一个性能较好的模型。在测试集上，该模型取得了约98%的分类准确率，与现有的深度学习框架相比具有竞争力。
### 5.3 分析与讨论
本实验通过自主实现反向传播算法和神经网络模型，成功地对MNIST数据集进行了分类。实验结果表明，通过调节超参数和采用合适的优化策略，三层神经网络就能够达到较好的性能。然而，由于时间和计算资源的限制，本实验只尝试了有限的超参数组合。在后续工作中，可以尝试更多的超参数组合和更复杂的模型结构，以进一步提高模型的性能。
此外，本实验只使用了简单的数据预处理和增强技术。在后续工作中，可以尝试使用更高级的数据预处理和增强技术来进一步提高模型的泛化能力。同时，也可以尝试使用更先进的优化算法和正则化技术来进一步提高模型的训练效率和性能。
