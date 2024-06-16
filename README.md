## 森井电气（SEN-Electric）除湿机CH948B智能化改造，通过ESPhome控制接入homeassistant
![1](https://github.com/Griddz/SEN-Electric-dehumidifiaction/blob/6ef5363da97843999c010b8a77a2a6d41fb95b20/image/1_sen_electric_snap.png)
因为已经改造过一个德龙（delong）除湿机,森井除湿机改造简单得多，森井除湿机没有水泵排水功能。
### 改造思路
- **本人非专业人士，项目仅作交流用。改造涉及强电，重则有生命危险，轻则损坏除湿机，本个概不负责，不承担任何法律责任！**
- 除湿机面板只有一个按键，这个按键是是一个循环按键，连续按就能切换到你需要的除湿状态，面板上有7个状态指示灯。通过继电器来模拟这个按键。拆开机器可以看到电路板的按键背面有四个锡焊点，接其中两个点，一个点是与电路板接地相连的，如果不确定你可以用电线或摄子去短接两个点，除湿机有相应反应了，说明这两个点可以作为按键模拟的接线点。
- 电路板上有7个Led小灯，分别来表明各种状态，测量LED灯两脚的电压是3V，直接可以用来接ESP32开发板的引脚作为状态反馈。我接了其中的6个，分别为关机、适湿、干爽、干燥、连续除湿、水满状态。除霜状态没接入，因为这个LED灯边上有个电容不太好焊接。
- 通过万用表测量，找到电路板5V的供电点，具体位置见下面的图片。

### 达成的效果
- 可以通过Homeassistant来控制开关、设定各种除湿模式并且有实时的状态反馈。同时没有破坏原有的手动控制功能。
- 缺陷：
      未能接入除湿机自带的湿度传感器。


###  森井电气（SEN-Electric）除湿机照片
![3](https://github.com/Griddz/SEN-Electric-dehumidifiaction/blob/6ef5363da97843999c010b8a77a2a6d41fb95b20/image/3_product.JPG)

### 材料：
1. 森井电气（SEN-Electric）除湿机型号：CH948B
2. 配件：
-    ESP32开发板一个（有5V供电脚）
-    5V小型继电器模块1路一个
### ESP32接线说明：
#### 按纽：
1. power_button <----------> GPIO21
#### 二进制状态线：
1. 1machine_on <----------> GPIO26
2. 2comfort_humidity  <----------> GPIO18
3. 3dry_comfort_humidity <----------> GPIO19
4. 5continuous_dehumidification <----------> GPIO27
5. 6water_full <----------> GPIO22
#### 图片
![22](https://github.com/Griddz/SEN-Electric-dehumidifiaction/blob/6ef5363da97843999c010b8a77a2a6d41fb95b20/image/2_finish.JPG)
![23](https://github.com/Griddz/SEN-Electric-dehumidifiaction/blob/6ef5363da97843999c010b8a77a2a6d41fb95b20/image/4_pcbline.JPG)
![25](https://github.com/Griddz/SEN-Electric-dehumidifiaction/blob/6ef5363da97843999c010b8a77a2a6d41fb95b20/image/5_pcbline2.JPG)
### 感谢@亮亮和@一切若然等人的帮助！！

