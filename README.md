执行一例复杂查询—————聚合查询，COUNT()：计数；SUM()：求和；AVG()：求平均值；MIN()：求最小值；MAX()：求最大值；COLLECT()：收集列表；PERCENTILE_CONT()：连续百分位数；PERCENTILE_DISC()：离散百分位数；STDEV()：样本标准差；STDEVP()：总体标准差
将Nod2Vec示例数据集导入TuGraph，运行采样数据成功
完整实现算法过程中主要用到了以下方法：Node2Vec有偏随机游走、邻居缓存、TuGraph只读事务接口；配置过程中遇到了以下问题：将脚本放入插件目录后，调用 CALL plugin_name() 时提示未找到插件，原因是TuGraph 要求插件文件必须放在指定的插件目录（如 build/output/plugins/），且文件名和函数名需符合规范（本例中入口函数必须为 Process(db, input)）。解决方法是确认插件目录路径，将脚本重命名为 node2vec.py 并重启 TuGraph 服务；同时在控制台执行 CALL db.plugins() 查看已加载的插件列表
