# 上海大学 计算机硬件综合大型作业
## 项目二 交通灯控制器
# 项目要求
十字路口，每面3个灯+二位数码管倒计时显示
# 快速入门
下载文件，安装Quartus，打开项目文件即可食用
# 目录说明
```
├─ traffic_led          // 项目的ModelSim仿真文件的文件夹，应该转移至与项目工程平行的目录下
├─ traffic_led.qpf      // 项目的工程文件
├─ traffic_led.bdf      // 电路图
├─ traffic_led.bsf
├─ traffic_led.v        // 顶层模块文件
├─ state_trans_model.v  // 控制器模块
├─ traffic_led_inst.v   // 交通灯模块
├─ led_module.v         // LED灯模块
├─ bit_seg_module.v     // 数码管模块
├─ test.v               // 测试文件
```

# 主要功能
可设定亮灯时间
可设定不同亮灯模式（正常方式、单向绿灯、双向黄灯闪烁、双向红灯）
注意倒计时超过100秒情况下数码管的显示
# 注意事项
- 项目基于Quartus 13.1.0 Web Edition，已验收通过（但是老师其实不喜欢基于Verilog的）
- 加入了左转信号灯。每个路口都采用数码管显示倒计时（只有南北或东西直行方向有，左转则为亮灯提示）
- 通过Key和sys_rst_n的不同输入信号，切换亮灯模式
  - 【正常模式】对应的Key为1111，【南北方向绿灯模式】为1110，【东西方向绿灯模式】为1101，【黄灯模式】为1011
  - sys_rst_n为0时，为遇到紧急情况进入【红灯模式】，倒计时停止，Key值输入无效，此时交通灯变为全红灯，不受其他输入信号干扰
- 如需要修改倒计时时间，可直接修改state_trans_model.v中的parameter define
- 连接硬件时请选择100kHZ的时钟频率
- 因为实验箱一共就六个数码管，最终只使用4个数码管表示北和西的倒计时
- bit_seg_module.v 中的bit和segment是没有用的，因为实验箱可以直接接数码管，只用关心num_n_0,num_n_1,num_w_0,num_w_1即可
# 参考资料
本项目基于YANthinkn的SHU-Computer-Hardware-Major-Assignment，略加修改以满足课程要求，感谢其共享！
链接：https://github.com/YANthinkn/SHU-Computer-Hardware-Major-Assignment
