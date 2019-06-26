# Data Modelling

Note: This article is in the progress of translation. Thanks for your visit!

完成数据采集后，Edge的另一个核心功能就是按照云端定义的设备模型，将采集到的数据模型化，并映射到对应的设备上。

.. image:: media/image005.png
   :alt: 图：Edge数据处理流程
   
## 映射

EnOS Edge采集到的数据，可以分为采集点和控制点。

采集点是设备向云端上送的测点，如风速、电动机转速等。

控制点是云端向设备下发的测点，如设备的启动、停止、复位等，控制点又分为AO型，取值可为整型或其他数据类型；与DO型控制点，取值通常为整型。

采集点和控制点的数据类型有以下几种：

- AI：即模拟输入（analogous input）
- DI：即数字输入（digital input）
- PI：即脉冲输入（pulse input）
- AO：即模拟输出（analogous output）
- DO：即数字输出（digital output）


对于采集点的映射，用户有以下映射方式：
- 一对一映射：采集点的值无需任何处理即成为模板属性点的值。在采集点列表中，为模型属性选择相应的采集点即可。
- 公式映射：对采集点进行公式运算，再映射到模型的属性上。EnOS为用户预置了一系列公式，参见[公式映射](../../reference/mapping_formula)
- 自定义脚本处理：对于复杂的数据处理，用户还可以通过自定义脚本的方式实现运算。

对于控制点的映射,用户只能采用简单映射方式。同一个模型点，既可以关联采集点，又可以关联控制点。

原始数据经过运算、映射处理后，变成标准的设备模型数据点，然后上送到EnOS。