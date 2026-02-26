放电boost30V

![8c9c02854d6a40f1c41be4511af78913](https://github.com/user-attachments/assets/59092770-f30a-4e77-92e4-b02eb6924493)

https://github.com/user-attachments/assets/6cd5b974-2195-4362-ae3e-edbf3dcc64fc

充电0.5A

![e817046c339c06fd3b7adc0f0e104bfa](https://github.com/user-attachments/assets/df27e07f-155c-493b-91ec-ea96f0f66c99)

https://github.com/user-attachments/assets/5c10ce5e-a392-4d7d-a5ee-07d570d73f47

Allegro绘制原理图

<img width="1045" height="737" alt="DCDCPCB" src="https://github.com/user-attachments/assets/966e1787-c910-4fc3-bf1e-2dcf4f5c3fff" />

电路分析

<img width="707" height="163" alt="image" src="https://github.com/user-attachments/assets/cb8d7c49-324e-4bc3-991b-2fa289ea4e42" />
<img width="488" height="128" alt="image" src="https://github.com/user-attachments/assets/f0236d1b-5fe1-4952-a76d-fe1449d7dc45" />

12V电源输入，经过电容滤波和LM2596S芯片开关电压输出降压为5V在经过L1电感储能和滤波电容输出，D4肖特基二极管为防止芯片开启时电感反向输出时破坏电路，反向回复电流，芯片关闭时电感反向经过电流，L1电感能减少电流突变浪涌
芯片选型LM25996S-5.0 散热好，成本低，输出电流适中，输出电压稳定

<img width="576" height="147" alt="image" src="https://github.com/user-attachments/assets/8698738e-fb79-4a86-a1b8-2b93d09f85af" />

下面电源经过连接端子通过LED灯确保电流经过

<img width="411" height="204" alt="image" src="https://github.com/user-attachments/assets/e32c6bf0-c8ce-45ed-8c15-5ece06038642" />

5V电容滤波后经过AMS1117-3.3再经过高低滤波电容输出3.3V   
选型AMS1117-3.3是成本较低，散热要求不高，精度满足

<img width="516" height="157" alt="image" src="https://github.com/user-attachments/assets/e4d63f52-cfbe-462c-bc52-0598cb1e5c13" />
<img width="296" height="272" alt="image" src="https://github.com/user-attachments/assets/dc711f8e-5e11-43ac-b743-151f2a83ebc0" />
<img width="865" height="584" alt="image" src="https://github.com/user-attachments/assets/4e13ff22-16a5-4df0-aace-27ca9dacd424" />

STM32模块 输出PWM和SD  接受电压和电流数据输出到OLED显示屏

<img width="865" height="603" alt="image" src="https://github.com/user-attachments/assets/cb47b109-d264-4c24-9546-a54f9c6df282" />

C66和两个并联电阻形成低通滤波电路滤除电源的高频干扰   
25的10mΩ采样电阻，小压降提高电流检测检测精度   
75和74的9R1电阻使差分输入阻抗相等与C66构成RC滤波，消除干扰，防止损坏芯片   
相比小电阻限流大，大电阻分压小   
D6保护单片机   
双向电流高端检测选型INA282AIDR，内置20倍固定增益，无需额外增益电阻，共模抑制比大，能有效抑制电源波动、地线噪声等共模干扰，精度高，5V提供基准电压，手册电路直接5V转2V上下

<img width="865" height="366" alt="image" src="https://github.com/user-attachments/assets/e5fc4bcb-e4ae-49d2-a333-70c5293102e3" />

前一个同相比例基本运算电路输入，经过运放电压衰减20倍，再经过，第二个电压跟随器直接输出电压，电压跟随器输出电阻小，电压全部输出到单片机   
5V提供运放静态工作电压

<img width="379" height="330" alt="image" src="https://github.com/user-attachments/assets/191f6868-eda2-4547-b4be-719d1f2c895f" />

STM32输出高低电平到DCOUT，通过DCOUT高低电平控制Q4三极管的导通，导通时5V输入，LED灯亮，线圈带电使2和5连接，输出低BE电压小于发射极开启电压，Q4断开，灯灭，线圈不带电

<img width="661" height="249" alt="image" src="https://github.com/user-attachments/assets/2f560c16-1c8d-44be-bbb3-0eab0ddb5ea4" />
<img width="307" height="83" alt="image" src="https://github.com/user-attachments/assets/aded70f9-4540-4d01-acd7-4089787d733a" />


STM32控制PWM和SD的输出，通过IR204STRPBF和VS1和VS的电流和C49自举电容和D5肖特基二极管来控制HO和LO高低电流转换来控制Q1和Q2的通断来实现buck boost操作   
L2磁珠率高频电流 U34电感储能和防止电流突变
二极管快速拉低G S电压
电阻消耗寄生电容电压

![d73124e44caca56c54a104e5e6cde7dd](https://github.com/user-attachments/assets/51b0ea91-f595-4cce-94b1-4b673b390d43)

电感电压为输入一半峰值电流最大
1mH纹波系数小，滤波效果好，缺点体系大

![a3f18cad4ff8b64af1148190e4b206bf](https://github.com/user-attachments/assets/095efd64-34ef-4089-96cb-12aa3d724077)
![f84e8af9b1a83718baa9970df3f3af99](https://github.com/user-attachments/assets/e01210e7-7bf6-4b76-8f7f-aaf82e4dc2aa)
220UF电解电容并联减小ESR


<img width="530" height="189" alt="image" src="https://github.com/user-attachments/assets/edcf0e66-87f0-422b-b574-55df9660ad2b" />

![efd0d4ae9ad2cedb0a1be6c693d989b0](https://github.com/user-attachments/assets/549d9c4e-6544-4d7a-907b-0d49f436c959)


C49自举电容驱动内部mos管
输入1K电阻防止电流过大损坏芯片   

PCB布局

<img width="703" height="690" alt="DCDC原理图" src="https://github.com/user-attachments/assets/a7a33538-142c-4114-9378-c2fd06194c91" />
