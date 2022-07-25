# 简介
由jasonxue自制,部分原件参考了他人的设计

现已完成:数电加法器,模电减法器
# 原理
## 数电加法器
### 1.0
拉杆选择器输入0-9,直接编码转换二进制(0000-1001)

二进制利用多个全加器进行加法运算

  全加器即为2个半加器,3无序输入+2有序输出(000-00,001-01,011-10,111-10)
  
  即将输入进行求和输出
  
  这里使用的全加器为2宽
  
  半加器可进行2者的求和,2无序输入+2有序输出(00-00,01-01,11-10)
  
  将两个半加器(2宽)进行前后连接,两个半加器的前输出口都要或门接入下一排的第二个半加器的输入口,第一个半加器的后输出口与此排第二个半加器的输入口进行连接即可,第二个半加器的后输出口为此全加器的输出口
