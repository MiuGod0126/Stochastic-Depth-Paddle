# 使用Paddle复现论文：Deep Networks with Stochastic Depth

[Deep Networks with Stochastic Depth](https://arxiv.org/pdf/1603.09382v3.pdf)

**前言**

- 由于训练深层网络经常会受到梯度消失、前层信息流消失、以及训练时间缓慢的问题，本文提出了随机深度的训练方法：在训练过程中随机去掉多层（对每一个batch，随机跳过几层输出到后面的网络），从而训练更小的网络，而在测试时使用全量更深的网络，相当于起到了集成模型的效果。

- 随机深度的训练方法显著减少了训练时间（训练时平均仅需训练原来模型的3/4），并且降低了cifar10验证错误率：使用110层resnet错误率为5.25%，1202层错误率降低为4.91%。

- 本项目实现了具有随机深度的残差网络，并用110层resnet在cifar10验证集上达到了5.18%错误率(准确率95.48%,500epoch)。

- 错误率比较：

  | who        | 110layer | 1202layer |
  | ---------- | -------- | --------- |
  | Kaiming He | 6.41%    | 6.67%     |
  | this paper | 5.25%    | 4.91%     |
  | me         | 4.52%    | -         |

  还等什么！让我们一起硬train一发！（硬train1202层的只需把配置中layers改为1202）

## 1.Tree

```
# 目录结构
/Stochastic-Depth-Paddle
├── README.md
├── ckpt/ # 模型保存路径
├── conf
│   └── base.yaml  # 配置文件
├── main.py # 运行
├── models/
├── run.sh # 运行
├── scrips.py # 加载数据、训练、评估
└── utils # 日志
```

## 2.Train

**注：参数的设置都在conf下的yaml配置文件里**

```
python main.py --config ./conf/base.yaml --mode train
或
./run.sh 1
```

## 3.Evaluate

```
python main.py  --config ./conf/base.yaml --mode eval
或
./run.sh 2
```

## 4.Link

- res110权重
  - 百度网盘链接：https://pan.baidu.com/s/1jURowo9yzTs-_Sy0wc4ibQ  提取码：spr5
  - 下载后放到工作目录的ckpt文件夹下
- [aistudio Stochastic Depth Paddle复现](https://aistudio.baidu.com/aistudio/projectdetail/2262209?shared=1)





