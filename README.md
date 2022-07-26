# 简介
由jasonxue自制的mc基岩版红石计算器  
存档在[***Releases***](https://github.com/jasonxue1/MCBE-Redstone-Calculator/releases)中下载  
这里的版本号规则在[***此处***](https://github.com/jasonxue1/MCBE-Redstone-Calculator/blob/main/resource/version.md)
布线稍加改变后java版也可使用  
部分原件参考了他人的设计,我已完全署名原作者,未标注的均为我自己所设计(如有雷同,均属巧合)  

现已完成:[***数电加法器***](https://github.com/jasonxue1/MCBE-Redstone-Calculator/blob/main/README.md#%E6%95%B0%E7%94%B5%E5%8A%A0%E6%B3%95%E5%99%A8),[***模电减法器***](https://github.com/jasonxue1/MCBE-Redstone-Calculator/blob/main/README.md#%E6%A8%A1%E7%94%B5%E5%87%8F%E6%B3%95%E5%99%A8)
# 原理/流程
## 数电加法器
### 1.0.0
仅支持1位运算  
2台拉杆选择器输入`0-9`(两个加数)  
8台1进4出编码器转换二进制(`0000-1001`)  
利用4个全加器进行加法运算  
这里的全加器采用了[***此视频中的设计***](https://www.bilibili.com/video/BV1xK411J76y)  
我写了一个[***全加器的介绍***](https://github.com/jasonxue1/MCBE-Redstone-Calculator/blob/main/resource/qjqjs.md),可以参考

第4个全加器的前输出口为第五位结果  
输出的取值为`0-18`(`00000-10010`)  
19台4进1出译码器转换为十进制对应的数字,这里的译码器采用了[***此视频中的设计***](https://www.bilibili.com/video/BV1Xt4y1S7UT)  
9台1进8出立体编码器转换为显示屏格式(个位7个口,十位由于要么1要么0,1个口即可解决)  
直接接入显示屏即可

具体布线见存档

如果进行更多位数的加法,还需对bcd和bin进行相互转换,较为麻烦,未来有可能完成
## 模电减法器
### 1.0.0
仅支持1位运算,暂不显示正负号,应该会在1.1.0版本加入  
2台拉杆选择器输入`0-9`(两数相减,但拉杆之间没有空隙)  
0旁边有电源激活,保证没有输入项时直接输入0,以免输入时显示错误  
拉杆后的方块后铺了红石线,红石线末端会根据输入不同导致等级不同(输入0时或不输入为6,输入1时为7……输入9时为15)  
用比较器进行信号延续  
使用比较器的减法模式进行相减  
上减下和下减上都需制作  
将两者的结果直接合并,即取较大的  
**重要:在走线时不能造成上下不等的信号强度损失,否则会出错**  
将结果用红石线输出,变为输出几就延长几格  
红石线旁边使用9个非门+与门单片让只有该单片的输入口为0信号时输出信号,否则不输出信号  
红石线前找一个合适地方使用一个非门使结果为0时输出信号  
使用10台立体单片1进7出编码器(和[*数电加法器*](https://github.com/jasonxue1/MCBE-Redstone-Calculator/blob/main/README.md#%E6%95%B0%E7%94%B5%E5%8A%A0%E6%B3%95%E5%99%A8)中的立体1进8出编码器)  
这个编码器参考了[***此视频中的设计***](https://www.bilibili.com/video/BV1ui4y1j7fW)  
后接显示屏即可  
由于编码器的输出口和显示屏之间的距离过于狭小,这里的布线就十分困难

由于目前版本没有加入正负显示模块,输入`a`和`b`时,输出`c=|a-b|`,取值为`0-9`

具体情况见存档
