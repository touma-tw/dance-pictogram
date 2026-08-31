# Dance Pictogram — 使用说明

跳舞时,视频旁边会滚动一条动作提示,在每个动作发生的前一刻告诉你接下来要做什么。
为 VRChat 的 [PyPyDance](https://pypydance.com/) 而做。

**语言:** [English](en.md) · [繁體中文](tc.md) · 简体中文 · [日本語](jp.md) · [한국어](ko.md)

---

## 1. 安装

1. 到 [Releases](https://github.com/touma-tw/dance-pictogram/releases) 下载最新的
   `DancePictogram-x.y.z.zip`。
2. 解压到任意位置,放桌面也可以。**不要放在 `C:\Program Files`**,程序会把歌曲数据写在自己旁边。
3. 运行 `DancePictogram.exe`。

不需要安装程序、不需要账号、不需要密钥。要卸载的话,直接删掉整个文件夹。

## 2. 下载歌曲

程序本身不含歌曲数据。打开 **Songs** 标签页。

**最快的方式** — 按上方的下载包按钮:

| 按钮 | 内容 |
|---|---|
| **Pictogram** | 手绘人形加上动作箭头。全部 598 首共 851 MB。 |
| **Real dancer** | 从视频中抠图取出的真人舞者,叠上同样的箭头。1632 MB。 |
| **Everything** | 两种都要。2244 MB。 |

然后按 **Download selected**。需要几分钟,期间可以继续操作程序。

**只挑几首** — 在搜索框输入后按回车,勾选想要的歌,再按 **Download selected**。
程序只会下载那几首,不会抓整包。

搜索支持普通关键词(曲名、歌手、曲风、编号),也可以组合条件:

```
twice                 任何匹配「twice」的
artist:twice          只找这个歌手
mode:multi            有多位舞者可选的曲目
genre:kpop            按曲风
installed:no          还没下载的
```

全部装完之后,下载包按钮会自动收起。点标题栏可以再展开。

## 3. 在 VR 里设置

切到 **Overlay** 标签页,按下大大的 **Start**。接着在 VRChat 里:

- **VR distance** — 提示条浮在多远的地方。建议推到跟视频屏幕差不多的深度,这样眼睛不用在两者之间重新对焦。
- **VR scale** — 看起来多大,与距离无关。
- **Pin in room** — 把提示条固定在空间中,不再跟着头转。
- **Pictogram / Real** — 显示哪一种图。

另外在你**右手手背**上会浮着一个小面板。看着按钮一会儿就会按下去 —— 因为 VRChat 占用了手柄,
只能用视线操作。上面有 **PIN**(不用摘下头显就能重新摆放提示条)和 **STYLE**。

## 4. 跳舞的时候

程序会读 VRChat 的日志来判断现在播的是哪一首,并且听你的扬声器来判断播到第几秒。
你不需要告诉它任何事。

**多人舞曲**会给每位教练一条轨道。开始时眼前会出现选择界面 —— 盯着你想跟的那位看两秒即可。

**觉得时间差一点?** 调整 `config.toml` 里的 `video_lag_sec`,或者直接告诉我们。
正值会让提示晚一点出现,负值会早一点。需要预备动作的提示,早一点出来反而好跳。

## 5. 用 OBS 录制

SteamVR 的 overlay 是叠在 VRChat 画面之上的,所以 VRChat 自己的摄像机看不到这条提示。
请在 Overlay 标签页打开 **Spout → OBS**,然后在 OBS 新增 **Spout2 Capture** 源,选择
`DancePictogram`。把它叠在 VRChat 摄像机源上方,并把合成模式设为 straight(非预乘)alpha。

## 6. 遇到问题

**提示条是空的。** 说明没有音乐在播,或程序听不到。请检查 Overlay 标签页的音频设备 ——
应该选择播放 VRChat 声音的那个设备的 **loopback(回放)**。

**显示的是别的歌。** 程序读 VRChat 日志判断曲目;如果 VRChat 没开,它会退而用声音识别,
而声音无法分辨那些用同一首音乐、但编舞不同的曲目。

**某一首的提示不准或时间不对。** 这确实会发生 —— 提示是自动生成的,遇到快速剪辑、
运动模糊、或多位舞者交错的视频,质量会比较差。请
[提一个 issue](https://github.com/touma-tw/dance-pictogram/issues) 并附上曲目编号。
重新生成的曲目会随之后的批次更新,程序只会下载有变动的部分。

**更新。** 程序启动时会检查有没有新增或修正过的曲目。Songs 标签页会显示哪些有变动,
按 **Install everything missing** 即可。
