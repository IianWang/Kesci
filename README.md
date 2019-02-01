# Kesci
# 信用卡欺诈检测-逻辑回归应用
## 项目背景：<br>
信用卡支付为日常生活中常见的一种支付方式。当然，交易中也会存在着欺诈(信用卡被盗刷)行为。如果可以利用机器学习完成对欺诈情况的预测，有助于发卡机构实现反欺诈，保护持卡人的财产安全。<br><br>
也就是说给出过往的信用卡部分数据（带标签）。通过观察数据找到可行的模型对数据进行拟合分类，用训练好的模型对测试数据集（无标签）进行预测。实现我们对信用卡欺诈行为的判断，帮助客户（发卡机构）准确判断持卡人是否非本人或在进行恶意的盗刷行为等。<br><br>

## 数据说明：<br>
|数据集名称 |数据类型 |特征数 |实例数 |值缺失 |相关任务 |
| --------   | -----:   | :----: | :----: | :----: |  :----: |
|信用卡欺诈检测数据集 |数值数据 |31 |284807 |无|不平衡样本处理，预测分类 |

<br>
* 在284807条交易记录中共包含492条欺诈记录。显然，数据集是不平衡的，欺诈这个类别仅仅占了0.172%。<br>
* 数据集仅包含数值型的变量是因为做了PCA变换。特征V1,V2,...V28分别是通过PCA变换得到的主成成分。<br>
* 没有做PCA变换的变量是 Time 和 Amount <br>
* 属性描述<br>
文件 creditcardfraud.csv中包含31个字段，具体信息如下：<br>
每一行记录了一条交易。<br>

|**No** |**属性** |**数据类型** |**字段描述** |
| --------   | -----:   | :----: | :----: |
|1 |Time |Float |数据集中第一条记录与本条记录的时间差值(seconds elapsed),秒为单位 |
|2 |V1 |Float |主成成分1 |
|3 |V2 |Float |主成成分2 |
|4 |V3 |Float |主成成分3 |
|5 |V4 |Float |主成成分4 |
|... |... |... |... |
|29 |V28 |Float |主成成分28 |
|30 |Amount |Float |该条交易记录的金额 |
|31 |Class |Float |类别是否为欺诈：1-是，0-否 |


<br>*导入数据，查看数据前5行*<br>
`df = pd.read_csv('/home/kesci/input/fraud_detection/creditcardfraud.csv')`<br>
`df.head()`<br>

|Time         |V1       |V2       |~       |V27    |V28    |Amount    |Class    |
| --------   | -----:   | :----: | :----: | :----: |  :----: |  :----: |  :----: |
|0.0         |-1.359807       |-0.072781       |……      |0.133558    |-0.021053    |149.62   |0    |
|0.0         |1.191857        |0.266151      |……      |-0.008983   |0.014724   |2.69  |0    |
|1.0         |-1.358354      |-1.340163       |……      |-0.055353  |-0.059752   |378.66  |0    |
|1.0         |-0.966272      |-0.185226      |……      |0.062723  |0.061458   |	123.50  |0    |
|2.0         |-1.158233      |0.877737      |……      |0.219422  |0.215153   |	69.99  |0    |
