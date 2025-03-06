# 创建模型
## 第一步 读取表格数据
```
import pandas as pd

melbourne_file_path = './melb_data.csv'
melbourne_data = pd.read_csv(melbourne_file_path) 
melbourne_data.columns
```
## 第二步 设定目标y值和特征X值
将需要拿来训练的列，作为训练的特征值
将训练要得到的结果，作为训练的目标值
例如：预测房价
目标值y-房子的价格
特征值X-房子的平方数、房子的房间数量、卫生间数量等

```
#将表格中的"Price"列做为目标值
y = melbourne_data.Price

#将['Rooms', 'Bathroom', 'Landsize', 'Lattitude', 'Longtitude']几列作为特征值
melbourne_features = ['Rooms', 'Bathroom', 'Landsize', 'Lattitude', 'Longtitude']
X = melbourne_data[melbourne_features]
```
## 第三步 创建模型，训练模型
创建模型：通过sklearn库中已有的方法直接创建一个实例
训练模型：将训练的数据也就是特征值和目标值放入到模型实例中
```
from sklearn.tree import DecisionTreeRegressor

#创建一个实例
melbourne_model = DecisionTreeRegressor(random_state=1)

#传入训练数据，训练模型
melbourne_model.fit(X, y)
```
## 第四步 通过训练后的模型预测数据
将需要预测的数据（也就是特征值）放入到已经训练过的模型中得到目标值
```
# X就是需要预测数据的特征值
melbourne_model.predict(x)
```