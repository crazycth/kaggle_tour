# kaggle_tour
尝试着记录kaggle的一些旅程

## Digit Recognizer

手写数字识别作为Kaggle的入门

关于分类问题其实方法很多，一路学习下来从AlexNet、VGG、GoogleNet到一招吃遍天的ResNet

不过这个 (1,28,28) 的输入即使不卷积直接fc也能得到很好的效果

在此使用自己写的ResNet练手（这为后边埋下了一个大坑）



最终得到正确率  0.99282 337/1795  😃

## Dog breed identification

尝试着对狗的种类进行分类

可能是打ACM留下的习惯，面对不是很难实现的算法/思想还是想自己手写来实现。但自己写的BottleNeck始终感觉处于过拟合的状态，在loss达到0.0004的情况下验证集准确率只有9%。

一直以为是自己写的有问题，找这个问题从下午三点弄到第二天（神经网络果然难debug☹️。今天才看到一个真正说服我的理由

> 我们被赋予一个深度学习任务时，比如说，一个涉及在图像数据集上训练卷积神经网络（Convet）的任务，我们的第一直觉就是从头开始训练网络，然而，实际上，从上图可以看到，神经网络会有大量的参数（Parameters），通常在几百万的范围内。在小数据集（小于参数数量）上训练CNN会极大影响CNN的泛化能力，通常会导致**过度拟合**。

在载入torchvision.Res50后一切正常了起来（终于



训练发现在val上正确率还是上不去。而且最终要的结果是nn.CrossEntropyLoss()，我一直用的是交叉熵. 觉得现在的问题出在Transpose()一块，对图像进行的变化太少了。而且对batch进行批量化操作好不熟练..cfj催着去吃圣诞大餐，先胡乱提交一版等回来再看吧

