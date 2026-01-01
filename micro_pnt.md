## 微PNT (Micro PNT) 的含义

### Purpose
- 解释“微PNT”（Micro Positioning, Navigation, Timing）这一术语，满足项目需求的术语说明。
- 说明其与计算机视觉的关联：微型化PNT常与视觉/SLAM/视觉里程计结合，在无GNSS场景为摄像头提供稳定的位姿与时间基准，从而提升融合定位的鲁棒性。

### Background
微PNT强调在极小体积、低功耗、低成本封装中集成定位、导航与授时（PNT）能力。
典型代表是 DARPA μPNT 计划，旨在让设备在室内、地下或遭干扰遮挡时仍可自持获取位置、姿态/航向及高精度时间基准。

### Technical Details (Overview)
- 组件：微型惯性测量器件（MEMS IMU）、微型原子钟、气压/磁力等环境辅助传感器。
- 特性：无外部信号依赖的自持定位、抗干扰；低功耗、小体积，便于随身或嵌入式部署。
- 典型指标（目标）：
  - 封装尺寸：立方厘米级。
  - 功耗：数百毫瓦至1W以内。
  - 漂移性能：
    - 时长：数十分钟至数小时的无外部信号条件。
    - 目标：水平漂移常见研究目标 <10 m/h，位置误差希望保持在米级到几十米量级。
    - 影响因素：传感器组合、标定质量、环境扰动。
- 典型应用：无人机、机器人、士兵可穿戴设备、传感器节点，与视觉/雷达/里程计联合用于GPS拒止环境。

### References
- DARPA μPNT program (Micro-Technology for Positioning, Navigation, and Timing), program page: [https://www.darpa.mil/program/micro-technology-for-positioning-navigation-and-timing](https://www.darpa.mil/program/micro-technology-for-positioning-navigation-and-timing) （如链接失效，可通过 web.archive.org 搜索相应快照）
- Archived snapshot example: https://web.archive.org/web/20230101000000/https://www.darpa.mil/program/micro-technology-for-positioning-navigation-and-timing
- PNT（Positioning, Navigation, Timing）通用定义。
