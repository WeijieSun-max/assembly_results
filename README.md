# 三维点云自动装配


## 数据集

我们提供了官方数据集的下载链接： [Fusion 360 Gallery Dataset]: [装配体数据集](https://github.com/AutodeskAILab/Fusion360GalleryDataset/blob/master/docs/assembly.md#mesh). 

##  准备

- 安装所需的依赖包

- 下载数据集到以下目录: ```./data``` 

- 将.obj文件转化为.ply文件

```shell
python convert_obj_to_ply.py
```


在运行之前，目录中应包含以下文件：

```
├── data
│   ├── Assembly1
│   │   ├── part1.ply
│   │   └── part2.ply
│   │   └── ...
│   └── Assembly2
│       ├── part1.ply
│       └── part2.ply
│       └── ...
├── convert_obj_to_ply.py
├── dataset.py
├── inference.py
├── losses.py
├── model.py
├── README.md
├── train.py
└── utils.py
```

## 训练
训练脚本： ```train.py```.

#### 固定平移(19518_f220b68a装配体)

```shell
python train.py --root ./data --epochs 100 --batch_size 1 --lr 1e-3 --emb_dim 128
```
损失曲线
![Loss_curve](https://github.com/WeijieSun-max/assembly_results/blob/main/loss_curve.png)

+ 最初装配体
![gt](https://github.com/WeijieSun-max/assembly_results/blob/main/gt.png)

+ 平移后的装配体
![input](https://github.com/WeijieSun-max/assembly_results/blob/main/input.png)

+ 恢复的装配体
![pred](https://github.com/WeijieSun-max/assembly_results/blob/main/pred.png)


#### 平移+噪声+点云抖动(19518_f220b68a等10个装配体)
```shell
python train.py --root ./data --epochs 100 --batch_size 1 --lr 1e-3 --emb_dim 128
```
损失曲线
![Loss_curve](https://github.com/WeijieSun-max/assembly_results/blob/main/loss_curve10.png)

+ 最初装配体
![gt](https://github.com/WeijieSun-max/assembly_results/blob/main/gt10.png)

+ 平移后的装配体
![input](https://github.com/WeijieSun-max/assembly_results/blob/main/input10.png)

+ 恢复的装配体
![pred](https://github.com/WeijieSun-max/assembly_results/blob/main/pred10.png)

