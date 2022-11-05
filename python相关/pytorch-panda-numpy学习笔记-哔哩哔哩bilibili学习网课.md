```python
#独热编码
data = pd.get_dummies(data)
'''重点'''
'''
出问题了 这个get_dummies  会在原来的非字母的列后再添加，所以我的最后的标签其实变成在中间点的地方
'''
```

```python
#加一列
df.join
```

```python
'''tensofflw 判断是否GPU的几个方法'''

sess =tf.compat.v1.Session(config=tf.compat.v1.ConfigProto(log_device_placement=True))
#查看是否为GPU
tf.config.list_physical_devices()

#显示1 表示GPU可用
print("Num GPUs Available: ", len(tf.config.experimental.list_physical_devices('GPU')))

#这个也可以
from tensorflow.python.client import device_lib
print(device_lib.list_local_devices())

```

```python
'''pytorch 判断是否是GPU的几个方法'''
#返回当前设备索引
import  torch
torch.cuda.current_device()
#返回GPU的数量
torch.cuda.device_count()
#返回gpu名字，设备索引默认从0开始
torch.cuda.get_device_name(0)
#cuda是否可用
torch.cuda.is_available()

```





**panda  read data** 

```python
data = pd.read_csv('./Transactions.txt')
#问题： 数据挖掘 老师的数据 读出来是下面这种形式，然后用下面的代码 就解决了  挺神奇
'''
OD\tpasta\tmilk\twater\tbiscuits\tcoffee\tbrioches\tyoghurt\tfrozen vegetables\ttunny\tbeer\ttomato souce\tcoke\trice\tjuices\tcrackers\toil\tfrozen fish\tice cream\tmozzarella\ttinned meat    2\t0\t1\t0\t0\t0\t0\t0\t0\t0\t0\t0\t0\t0\t0\t0...
'''
#后来发现  老师的数据其实是这样的
COD	pasta	milk	water	biscuits	coffee	brioches	yoghurt	frozen vegetables	tunny	beer	tomato souce	coke	rice	juices	crackers	oil	frozen fish	ice cream	mozzarella	tinned meat
1	0	0	0	0	0	0	0	0	1	0	0	0	0	0	0	0	0	0	1	1
2	0	1	0	0	0	0	0	0	0	0	0	0	0	0	0	0	0	0	0	0
3	1	1	0	0	0	0	0	0	0	0	0	1	0	0	1	0	0	0	0	0
4	0	0	1	0	0	0	0	0	
#原来上面的 反斜杠是 panda读出来的 空格符或者是 换行符
'''
elim_whitespace
0.18 版本后新加参数，默认为 False，设置为 True 时，表示分割符为空白字符，可以是空格、"\t"等等。比如：girl.csv的分隔符是"\t"，如果设置delim_whitespace为True的话：
'''
#
data = pd.read_csv('./Transactions.txt',delim_whitespace=True)
```



数据挖掘 汇报数据各类指标

```python
from sklearn.metrics import confusion_matrix, classification_report, accuracy_score
# Result Evaluation
print("Classicfication report:\n",classification_report(y_test,preds))


Classicfication report:
               precision    recall  f1-score   support

           0       0.56      0.89      0.69      5043
           1       0.56      0.17      0.26      4206

    accuracy                           0.56      9249
   macro avg       0.56      0.53      0.48      9249
weighted avg       0.56      0.56      0.49      9249

print("Confusion Matrix:\n",confusion_matrix(y_test,preds))
print("\nAccuracy:",accuracy_score(y_test,preds))
```

