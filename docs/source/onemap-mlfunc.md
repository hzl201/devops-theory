### 一张图后台管理

> 主要适用于临矿。以下都是直接编辑mlfunc.js文件。



**加载图种分类设置**

> 根据不同矿井的图种分类来单独进行设置。
搜索function openTZ(tzmodulename, callback)
在下面找到需要单独设置的矿井
```shell
    else if (tzmodulename == '压风系统') {
        if (deptName == "王楼煤矿" || deptName == "郭屯煤矿" || deptName == "新驿煤矿") #有的矿井是压风管路系统图，把这些矿井名称填好
            tzName = "安全类^压风管路系统图";
        else
            tzName = "安全类^压风自救系统图";
    }
```

**修改另一个设置**

> 新加入的矿井需要设置。

搜索function InitModule_data_z(m_index, s_index, t_index)
在下面添加新的矿井,如&& deptName != "里彦煤矿"
```shell
                if (selectModuleName == "监测分站" || selectModuleName == "检测分站" || selectModuleName == "截止阀" || selectModuleName == "岩巷" || selectModuleName == "回柱绞车" || selectModuleName == "检测读卡器" || selectModuleName == "电话" || selectModuleName == "回采工作面") {
                    if (deptName != "郭屯煤矿" && deptName != "彭庄煤矿" && deptName != "新驿煤矿" && deptName != "里彦煤矿") {
                        Module_Data_z.sort(SortByProperty);
```


**显示人员轨迹**

> 新加矿井需设置。
搜索function print_rygj(stationID, trace)
在下面添加新矿井
```shell
    else if (deptName == "古城煤矿")
        person_layer = "人员定位路径GCK0000ARY";
    else if (deptName == "王楼煤矿")
        person_layer = "人员定位参考路径WLK0000ARY";
    else if (deptName == "里彦煤矿")
        person_layer = "人员定位路径LYK0000ARY";
    else if (deptName == "郭屯煤矿")
        person_layer = "人员定位路径GTK0300ARY";
    else if (deptName == "彭庄煤矿")
        person_layer = "人员定位路径PZK0303ARY";
    else if (deptName == "新驿煤矿")
        person_layer = "人员定位路径XYK0000ARY";
```



**掘进头危险源设置**

> 掘进工作面的危险源图层设置方法。
搜索function EarlyWarning() 
在下面添加新的矿井
```shell
    else if (deptName == "王楼煤矿") {
        jjtlayer = "掘进工作面";
        dangerlayer = "断层,已采采空区";
        jjtkey = "USER__CUSTOMPROPERTY_中文名称";
    }
    else if (deptName == "鲁西煤矿") {
        jjtlayer = "掘进工作面";
        dangerlayer = "村庄,保护煤柱";
        jjtkey = "USER__CUSTOMPROPERTY_掘进头名称";
    }
    else if (deptName == "新驿煤矿") {
        jjtlayer = "掘进头";
        dangerlayer = "陷落柱,村庄,井田边界,断层,保护煤柱";
        jjtkey = "USER__CUSTOMPROPERTY_掘进头名称";
    }
    else if (deptName == "郭屯煤矿") {
        jjtlayer = "掘进工作面";
        dangerlayer = "陷落柱,村庄,井田边界,断层,煤巷,保护煤柱";
        jjtkey = "USER__CUSTOMPROPERTY_掘进头名称";
    }
    else if (deptName == "彭庄煤矿") {
        jjtlayer = "掘进工作面";
        dangerlayer = "陷落柱,村庄,井田边界,断层,保护煤柱";
        jjtkey = "USER__CUSTOMPROPERTY_掘进头名称";
    }
    else if (deptName == "里彦煤矿") {
        jjtlayer = "掘进工作面";
        dangerlayer = "陷落柱,村庄,井田边界,断层,保护煤柱,积水区,岩巷,煤巷,钻孔"; #主要修改这些图层名称关键字
        jjtkey = "USER__CUSTOMPROPERTY_掘进头名称";
    }
```