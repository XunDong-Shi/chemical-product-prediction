# chemical-product-prediction
此文件为DC竞赛化工产品品质预测算法竞赛的代码，因主办方要求不可下载服务器上的数据，故本算法中无数据输入。
本人正对数据分析与挖掘学习，欢迎各位高手指正、沟通！
算法介绍如下：
1.  将训练集与测试集固定时间间隔的数据融合到一起；
2.  根据文献的阅读和工艺分析，对各个预测结果的特征进行了筛选，并新增了总压力、返料比、中和度等新特征；
3.  对明显出现异常的传感器数据进行清洗：去除了成品质量和返料质量的异常时间段内的数据；
4.	通过数据探索，估计出从入料至检验的时间间隔约为7小时左右。故以此为依据，采用样品检验间隔中的时间段，并向前平移7小时得到所对应生产时间内的传感器数据，对该时间段内的传感器数据取平均值。
5.	因存在返料，所以下一时段的含量数据（氮含量、磷含量、总营养、水分含量）与上一时段有一定关系，所以将上一时间段的含量数据加入到本时段预测的因素中；
6.	进行归一化处理；
7.	以xgboost，svr，ela和gbr为第一层，knr为第二层的stacking模型进行训练，得到回归模型。

