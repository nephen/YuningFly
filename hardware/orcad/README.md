#OrCAD说明

本文为设计原理图的过程记载。

通过查看px4官方原理图可以发现，主处理器为stm32f427，在FMU SoC Ports FRAM这页可以发现，协处理器为stm32f103，在IO SoC Ports Spektrum/DSM port这页可以发现。其中处理器是以端口的形式出现在相应类别的页码中，而不是以我们平常画原理图芯片元件整体的形式，所以注意理解这个。

电源流行分析：电流计出来的VDD_5V_IN -> 分流为IO-VDD_5V5,VDD_5V_PERIPH和VDD_5V_HIPOWER，但是我们舍弃了VDD_5V_HIPOWER，而VDD_5V_PERIPH用于给外接器件供电 -> 然后VDD_5V_PERIPH还通过稳压芯片转换出FMU-VDD_3V3和IO-VDD_3V3，FMU-VDD_3V3给stm32f427及传感器供电，IO-VDD_3V3给stm32f103供电。

更多参考[pixhawk飞控介绍](http://www.docin.com/p-1092528341.html)/[看看pixhawk的无赖设计](http://www.docin.com/p-757319248.html)

1. 建立工程

	![creat_project](../images/creat_project.png)

2. 添加[标题栏](http://jingyan.baidu.com/article/e52e36154467e940c60c5187.html)TitleBlock0

2. [新建元件库](http://wenku.baidu.com/link?url=DZptfwWOgny_4ejvw0WVvdqtp3VgsoHT-yGHt6wsm5c1NJOCFY3XP785GMzvEdvsZaiIEJOPT90HGhJvafOW3MPGFWrTl4v8kh2h3J7UwQ7)yuningfly.OLB，并创建新在元件如：stm32f407

	![place](../images/Place.png)

	当你在创建页面更改了元件，需要在原理图中更新时，点击Update Cache进行更新即可

	![update_com](../images/update_com.png)

3. 添加元件库

	![addolb](../images/addolb.png)

4. 放置元件到原理图，如果能记住元件在名字可以进行全局搜索，万一不记得上网搜索如晶振为CRYSTAL，或者直接在库里进行查找，如常用的库为DESCRETE

	![place_com](../images/place_com.png)

5. 如果原理图页面过小，可以修改原理图的大小

	![fix_size](../images/fix_size.png)

6. 连线，可以使用快捷键w，注意这里不能为红色，否则线连的不是很整齐。

	![white](../images/white.png)