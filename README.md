# 某公司客户-工业瑕疵检测
## 项目简介
本项目基于优化的Mask RCNN网络进行工业瑕疵品检测  

本项目在Mask RCNN基础上结合了：  
　　Relation Network模块  
　　Global Context全局特征  
　　DCN可变卷积  
　　随机图像增强  
有效提升了瑕疵检测效果和泛化性  
  
本次实验所用到的数据总共1571张图片18个类别（17种瑕疵+1个正常），按照7:3划分训练测试集进行训练  
最终在测试集上达到96.82%的准确率和83.3%的mAP，混淆矩阵如下：  
[[29  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0]  
 [ 1 24  0  0  0  0  0  0  0  0  0  0  0  0  0  0]  
 [ 0  0  8  0  0  0  0  0  0  0  0  0  0  0  0  0]  
 [ 0  0  0 25  0  0  0  0  2  0  0  0  0  0  0  0]  
 [ 0  0  0  0 55  1  0  0  0  0  0  0  0  0  0  0]  
 [ 0  0  0  0  0 40  0  0  0  0  0  0  0  0  0  0]  
 [ 0  0  0  3  0  0 38  0  0  0  0  0  0  0  0  0]  
 [ 0  0  0  1  0  0  1 33  0  0  0  0  0  0  0  0]  
 [ 0  0  0  0  0  0  0  0 15  0  0  0  0  0  0  0]  
 [ 0  0  0  0  0  0  0  0  0 29  0  0  0  1  0  0]  
 [ 0  0  0  0  0  0  0  0  0  0 23  0  0  0  0  0]  
 [ 0  0  0  0  0  0  0  0  0  0  0 17  0  0  0  0]  
 [ 0  0  0  0  0  0  0  0  0  0  0  0 25  0  1  0]  
 [ 0  0  0  0  0  0  0  0  0  1  0  1  0 31  0  0]  
 [ 0  0  0  0  0  0  0  0  0  0  1  0  0  0 35  1]  
 [ 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0 29]]  
precision: ['96.67%', '100.00%', '100.00%', '86.21%', '100.00%', '97.56%', '97.44%', '100.00%', '88.24%', '96.67%', '95.83%', '94.44%', '100.00%', '96.88%', '97.22%', '96.67%']  
recall: ['100.00%', '96.00%', '100.00%', '92.59%', '98.21%', '100.00%', '92.68%', '94.29%', '100.00%', '96.67%', '100.00%', '100.00%', '96.15%', '93.94%', '94.59%', '100.00%']  



## 项目部署
本项目可在Windows或Linux上进行部署运行  
环境要求如下：  
　　Windows或Linux  
　　Python 3.7及以上  
　　PyTorch 1.6及以上  
更多第三方库请见**requirement.txt**  
可通过命令 **pip install -r requirement.txt** 对这些库进行安装，也可逐一手动安装  

## 训练数据准备
若是要直接运行模型进行测试，可以跳过这部分  
若是要从头开始训练模型，则需要准备训练数据  
在本项目中数据已经准备好了，见`data/NP_pick_together`，若是有更多数据可以仿照这个格式来存放   
图像标注采用`labelme`软件进行标注，详情链接：https://github.com/wkentaro/labelme  
图片文件和标注文件的存放格式为：  
~~~~
data/  
　　dataset_1/  
　　　　img/  
　　　　　　xxx.jpg  
　　　　　　yyy.jpg  
　　　　　　...  
　　　　label/  
　　　　　　xxx.json  
　　　　　　yyy.json  
　　　　　　...  
　　dataset_2/  
　　　　img/  
　　　　label/   
　　... ...  
~~~~
其中dataset_x为数据集的名称，可自定义，只要在代码中也修改对应的数据集名称就可以  
接下来就可以运行以下命令来训练：  
`python train_relation.py`   
具体的参数设置见代码文件`train_relation.py`


## 项目运行
在这之前，我已经运行过并且把结果输出保存在了preds_output文件夹中  
其中，文件夹名是分类的类别，图片的文件名是原来的路径  
若要重新运行测试代码，可用此命令：  
`python eval.py`    

## 更新日志
20201209　　V1.0
