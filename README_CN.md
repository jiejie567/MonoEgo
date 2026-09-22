<div align="center">

# MonoEgo

**单目第一人称操作数据采集**

<a href="https://anyverse.com/"><img src="docs/images/anyverse-dynamics-logo.png" width="280" alt="无界动力"></a>

[MonoTag SLAM 源码](https://github.com/jiejie567/MonoTag-SLAM) · [硬件](hardware/README.md) · [实验结果](results/README.md)

</div>

[English](README.md) | 中文

MonoEgo 使用一台头戴 RGB 相机、两只无源腕带和工位上的已知尺寸 marker，录制操作视频，再离线重建米制相机与腕带轨迹。

腕带不需要电池、IMU 或无线模块。场景、手和 marker 都来自同一图像时钟，无需额外对齐独立手部追踪设备与视频。相机内参和腕带星座几何仍需要标定。

本仓库已公开，包含硬件、示例视频与紧凑实验结果；处理代码单独维护在 [MonoTag SLAM](https://github.com/jiejie567/MonoTag-SLAM)，代码仓库暂时保持 private，待后续发布。

![采集系统](figures/fig1_teaser_integrated_v5.png)

## 使用流程

![处理流程](docs/images/workflow.png)

打印和装配 → 核实 marker 尺寸 → 标定相机与腕带 → 录制原始视频 → 离线重建 → 检查有效性和轨迹 → 按需导出。

已知 marker 尺寸提供尺度，多帧几何共同约束地图。离线回溯只恢复证据充分的帧，不承诺所有视频都能从第一帧定位。可选的 marker 外观覆盖不会反馈到定位与标签生成。

## 硬件与文件

<p align="center"><img src="hardware/wrist_constellation_REV5/REV5_fit_preview.png" width="800" alt="REV5 双槽腕带与 marker 贴纸位置"></p>

默认使用 **REV5 双橡皮筋槽版，无磁铁孔**。[下载两瓣 STL 和配套 marker 打印文件](hardware/wrist_constellation_REV5/)。护腕内侧贴海绵，通过厚度适配不同腕围；两瓣扣合后，在上下两圈槽内各套一根橡皮筋固定。海绵不要夹进接缝，橡皮筋不要遮挡 marker。详见[装配说明](hardware/README.md)。

- [REV5 双槽腕带 STL、贴纸和标定板](hardware/README.md)。
- [已标定腕带布局示例](hardware/marker_layouts/calibrated_release/)仅对应实验中的实物；新装配应重新标定。
- [SW-02 示例](videos/SW-02_english_orb_trajectories.mp4)和 [SW-04 示例](videos/SW-04_english_orb_trajectories.mp4)展示相机移动、腕带静止时的轨迹。
- [相机参考与静止腕带结果](results/README.md)。

### 相机选择

**不限定品牌和型号**，主要关注三点：**高帧率、可手动控制曝光时间、较大的 FOV（视场角）**。画面应能同时覆盖双手和足够的周围场景。高帧率不等于短曝光：要根据运动速度设置足够短的曝光，并保证照明。FOV 也不是越大越好，应保留足够像素让腕带 marker 清晰可辨。

实测配置采用 WN-L2406K397L 全局快门模组、2.3 mm f/1.8 M12 镜头，录制 1080p / 90 FPS，仅作参考，不要求购买同款。快速运动时优先考虑全局快门，其他相机不保证达到相同实验结果。更换相机、镜头或录制模式后重新标定，录制时保持焦距、裁剪和防抖设置不变；算法使用标定内参。

所统计的采集侧 BOM 不到 100 美元，不含录制设备、替换镜头、计算机、小五金与耗材、人工和运费。

打印时关闭“适应页面”，实测黑色方形外边长。调节海绵厚度，使腕带稳定且不勒手；新装配或更换贴纸后应重新标定腕带。

## 实验解释

Odin 多传感器里程计用于相机参考，不是算法输入或独立认证的绝对真值。SE(3) 与消除全局尺度的 Sim(3) 指标分开报告，误差需结合覆盖率阅读。

四段静止腕带实验的单侧 RMS 散布约为 1.26–2.69 mm。这是静止条件下的精密度，不代表动态动作或解剖学手腕精度。

仓库不包含原始室内视频、私人屏幕内容、模型权重或机器私有配置。此次无模糊宣发审阅视频不上传仓库。

## 许可

原创硬件、布局、图稿、结果表和文档使用 [CC BY 4.0](LICENSE.md)，署名 MonoEgo — Anyverse Dynamics，并注明修改。公司 Logo 不包含在此许可中，第三方材料保留原许可。配套 SLAM 代码使用 GPL-3.0。
