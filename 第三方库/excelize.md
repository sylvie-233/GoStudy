# excelize


## 基础介绍

go excel操作库

基于File对象操作


## 核心内容
```yaml
excelize:
    Alignment:
    Cell: # 单元格
    Chart: # 数据图表
    Cols: # 数据列
    Comment: # 批注
    DataValidation: # 数据校验
    File: # 文件
        AddChart(): # 添加图表
        AddChartSheet(): # 添加图表工作表
        AddComment():
        AddDataValidation():
        AddPicture(): # 添加图片
        AddPivotTable():
        AddShape():
        AddSparkline():
        AddTable():  # 添加数据表
        CalcCellValue(): # 计算单元格公式
        Close():
        GetActiveSheetIndex():
        GetCellValue(): # 直接获取单元格值
        GetColWidth():
        GetComments(): # 获取所有批注
        GetMergeCells():
        GetRowHeight():
        GetRows(): # 获取所有数据行
        GetSheetList(): # 获取所有Sheet
        InsertRow(): # 插入空白行
        InsertPageBreak(): # 插入分页符
        MergeCell(): # 合并单元格
        NewSheet():
        ProtectSheet():
        Save():
        SavaAs(): # 另存为
        SearchSheet():
        SetActiveSheet(): # 设置默认工作表
        SetCellFormula(): # 设置单元格公式
        SetCellHyperLink():
        SetCellRichText():
        SetCellStr():
        SetCellStyle():
        SetCellValue(): # 直接设置单元格值
        SetColStyle():
        SetColVisible():
        SetColWidth():
        SetConditionalFormat():
        SetDifinedName():
        SetDocProps(): # 设置工作簿属性
        SetHeaderFooter():
        SetPanes(): # 设置窗格
        SetRowHeight():
        SetSheetBackground(): # 设置数据表背景
        SetSheetName(): # 设置数据表名称
        SetSheetRow(): # 设置表指定行数据
        SetSheetViewOptions(): # 设置数据表视图属性
        SetSheetVisible(): # 设置数据表可见性
    Fill:
    Font:
    MergeCell: # 合并单元格
        GetCellValue():
        GetEndAxis():
        GetStartAxis():
    Panes: # 视图窗格
    Picture: # 图片
    Rows: # 数据行
    StreamWriter: # 流式写入器
        AddTable(): # 
        Flush(): # 刷新写入
        MergeCell(): # 合并单元格
        SetColWidth():
        SetRow(): # 设置一行数据
    Style: # 单元格样式
        Alignment:
        Fill:
    Table: # 数据表
    ViewOptions:
    CellNameToCoordinates(): # 名称转坐标
    ColumnNumberToName():
    CoordinatesToCellName(): # 坐标转名称
    JoinCellName(): # 拼接单元格名称
    NewConditionalStyle():
    NewFile(): # 新建文件
    NewStreamWriter(): # 流式写入器
    NewStyle():
    OpenFile(): # 打开文件
    OpenReader():
```


### File

基础操作均是基于File对象


### Table


### Rows


### Cell