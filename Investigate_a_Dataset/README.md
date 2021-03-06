# 项目：探索调查未前往就诊的挂号预约数据集

## 目录<br>
    简介
    数据整理
    探索性数据分析
    结论
### 简介
    
本数据集包含10万条巴西预约挂号的求诊信息，包含了关于患者特点的数据，研究病人是否如约前往医院就诊。其中，“预约日期 (ScheduledDay)”指患者具体预约就诊的日期；“街区 (Neighborhood) ”指医院所在位置；“福利保障 (Scholarship)”说明病人是否是巴西福利项目 Bolsa Família 的保障人群；请注意最后一列内容的编码：“No”表示病人已如约就诊，“Yes”说明病人未前往就诊。

本文将研究有哪些重要因素能够帮助我们预测患者是否会按照其挂号预约前往医院就诊？主要会从患者的性别，年龄，福利保障这三点进行研究。

### 数据整理  
常规属性<br> 
        对数据集中的数据类型，是否有缺失值或异常值，是否有重复进行如下评估。<br> 
        说明：通过对数据集的探索，得出该数据集有110527行14列。无缺失数据，无重复数据行。数据集存在如下的问题： 1、数据类型错误：ScheduledDay和AppointmentDay类型为字符类型，应该更改为时间类型；数据集中的‘No-show’取值为Yes或No，为字符型，为方便后续直接对其进行运算，将其转换为布尔型。 3、存在异常数据：年龄列有一个-1值，由于数据样本充足，因此删除该值对应的样本。  <br> 

数据清理<br> 
        1、修改‘ScheduledDay’‘AppointmentDay’类型为时间类型<br> 
        2、修改数据集中的‘No-show’取值为Yes或No为布尔型<br> 
        3、删除年龄列中错误的样本<br> 
        4、‘ScheduledDay’‘AppointmentDay’两列已经更改为时间类型，增加一列差异时间,检查下就诊日是否会在预约日之前的的异常数据<br> 
        5、由于后续将对年龄进行分析，在此增加一列年龄分组  <br> 
### 探索性数据分析

对总体如约就诊和未去就诊的数据进行分析，得出如约就诊的比例是79.8%，未去就诊的失约比例为20.2%。后续将会对各个变量与总体失约比例进行探讨。对性别、年龄段、是否有福利保障探索其失约率。<br> 
        对性别得出结论：通过对性别，年龄，福利保障与患者是否如约就诊进行探索。可以得出性别与患者是否会按照其挂号预约前往医院就诊影响不大，年龄在10-20岁的患者容易失约就诊，福利保障为1的失约比例高，对其是否如约就诊有关系。因此，年龄和福利保障能够帮助我们预测患者是否会按照其挂号预约前往医院就诊。<br> 

### 结论
本报告主要探索了性别，年龄分布，是否有福利保障这三个因素与患者是否会按照其挂号预约前往医院就诊的关系。这些只是一部分，并不能完全代表结果，还可以从是否收到短信通知、就诊时间和预约时间的时间差和缺席率的相关性进行探究，观察这些因素能否帮助我们预测患者是否会按照其挂号预约前往医院就诊。<br> 
