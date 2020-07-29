# 在BI系统中使用百度地图

1.从睿思BI4.6开始，支持百度地图潜入bi系统中进行可视化展现，首先用户申请自己的百度地图AK（请注意：本公司并不提供百度地图AK，如果用户在商用项目中使用百度地图，需要购买商业授权）

2.在 ext-config.xml文件中配置百度地图AK

```
<!-- 百度地图的AK， 此AK只做测试使用，企业客户请申请自己的AK -->
<constant name="baiduMapAK" value="xxxxxx"/>
```

3.在仪表盘/报表的图表类型中选择百度地图。

![](/assets2/import20.png)

4.设置图形的数据，属性等内容，完成百度地图的可视化。请注意，在百度地图中显示的数据必须包含经纬度信息，现目前所有地域的经纬度信息都放在src/main/webapp/ext-res/js/chartjson/city-baidu.json文件中。如果您数据的地域信息不包括在此json文件中，请在此文件中添加。
