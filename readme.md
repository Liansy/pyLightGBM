LightGBM 的 issue上在讨论python binding，看到了这个quick wrapper pyLightGBM，实现挺简单的

- 在`models.py`里构造了GenericGMB类，继承了sklearn的BaseEstimator
- 构造函数里传入各种参数，然后写入 `train.config`
- fit函数里用python的 `os.system("./lightgbm config=train.conf")`去调用cpp 编译出来的可执行文件`lightgbm`

因为继承了sklearn的BaseEstimator，可以使用一些sklearn的特性，像cv，cross_val_score等
