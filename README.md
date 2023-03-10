# ClasstableToIcal
Convert Classtable to iCal using Pything and Excel as data source.

该工具可以方便地将课程表转换为 `.ics` 格式以导入各种设备的「日程」中。

> 提示：I forked this repository 来给安大的同学们提供更加便捷的导入功能
>
> conf_classTime.json已改为安大现行上课时间标准（第1-11节）
>
> 有问题欢迎在此repo或源repo提issue。

## Usage

以下为简略说明，更详细教程请参看[少数派](https://sspai.com/post/59694)。

先安装依赖：

```shell
pip install uuid xlrd 
```

然后执行 `main.py`：

```shell
python main.py
# or
python3 main.py
```

测试环境为：Python 3.7.2，Windows 10 x64.

## 文件中格式解释

### temp_classInfo.xlsx

课程的名称、起始周数等在文件里已标示清楚，weekStatus 是单双周标记。

> 0=不分单双周，1=单周，2=双周

是否显示教师、是否开启单双周功能可在 `excel_reader.py` 中更改。

### conf_classTime.json

```json
"1": {
    "name": "第 1 节", 
    "startTime": "082000",
    "endTime": "095500"
}
```

该文件为 JSON 格式，一开始的数字是**时段编号**，对应 `temp_classinfo.xls` 里的 `classTime` 字段；`startTime` 与 `endTime` 采用 `%H%M%S` 格式，即时、分、秒去掉分隔符。

## Feature

现在支持：

- 单双周排课
- 课前n分钟提醒（待进一步测试）
- 不同教室（添加多个条目）
- 跨时段上课（[Contributed by @BoisV](https://github.com/SunsetYe66/ClasstableToIcal/pull/4)），现在定义上课时间段的方式改为开始时间id + 结束时间id，可以应对更复杂的时间需求

## License

LGPLv3
