# 简介
由jasonxue自制的mc基岩版红石计算器  
存档在release中下载  
这里的版本号规则在[***此处***](https://github.com/jasonxue1/MCBE-Redstone-Calculator/blob/main/resource/version.md)
布线稍加改变后java版也可使用  
部分原件参考了他人的设计,我已完全署名原作者,未标注的均为我自己所设计(如有雷同,均属巧合)  

现已完成:[***数电加法器***](https://github.com/jasonxue1/MCBE-Redstone-Calculator/blob/main/README.md#%E6%95%B0%E7%94%B5%E5%8A%A0%E6%B3%95%E5%99%A8),***模电减法器***
# 原理/流程
## 数电加法器
### 1.0.0
仅支持1位运算  
2台拉杆选择器输入0-9(两个加数)  
8台1进4出编码器转换二进制(0000-1001)  
二进制利用4个全加器进行加法运算这里的全加器采用了[***此设计***](https://www.bilibili.com/video/BV1xK411J76y)  
我写了一个[***全加器的介绍***](https://github.com/jasonxue1/MCBE-Redstone-Calculator/blob/main/resource/qjqjs.md),可以参考

第4个全加器的前输出口为第五位结果  
输出的取值为0-18(00000-10010)  
19台4进1出译码器转换为十进制对应的数字,这里的译码器采用了[***此设计***](https://www.bilibili.com/video/BV1Xt4y1S7UT)  
9台1进8出立体编码器转换为显示屏格式(个位7个口,十位由于要么1要么0,1个口即可解决)

具体布线见存档

如果进行更多位数的加法,还需对bcd和bin进行相互转换,较为麻烦,未来有可能完成
