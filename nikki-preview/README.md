# InfinityNikkiAutoKey 脚本预听

一个用于预听 InfinityNikkiAutoKey 自动演奏脚本的本地网页工具。主要用途是在不上游戏的情况下检查脚本的节奏、音准和多线程配合。

## 打开方式

推荐用本地 HTTP 服务打开，否则内置音源可能因为浏览器安全限制无法加载。

在仓库根目录运行：

```powershell
py -m http.server 8000
```

然后访问：

```text
http://localhost:8000/nikki-preview/
```

如果直接双击 `index.html`，页面本身可以打开，但内置音源在 `file://` 或部分移动端 `content://` 环境下可能无法读取。此时可以改用“本地录音”手动选择音频文件。

## 音源

内置三套点按乐器音源：

- 竖琴：`nikki_record/harp`
- 里拉琴：`nikki_record/lyre`
- 钢琴：`nikki_record/piano`

每套音源按暖暖 21 键命名：

```text
Z X C V B N M A S D F G H J Q W E R T Y U
```

## 支持语法

已支持常用脚本语法：

- `instrument:`
- `$bpm`
- `$beat`
- `$delay-common`
- `$duration-common`
- `$delay-before`
- `$section-begin` / `$section-end` / `$section`
- `$loop-begin` / `$loop-start` / `$loop-end`
- `$thread-begin` / `$thread-end`
- `$legato`
- 普通键位、休止符 `_`、等待 `$4` / `$8.` / `$4~4` / `&8`
- `#` 单行注释、`---` 多行注释

## 使用说明

- 粘贴脚本后点击“播放”。
- “从光标播放”会从当前选区所在行或 `$section` 调用行开始。
- 多线程脚本会在右侧显示每个线程的轨道卡片，可单独启用或禁用。
- 顶部“拍数 当前/总拍数”显示的是音乐拍位，不是秒数。

## 适配范围

这个工具主要适配点按类乐器，例如竖琴、里拉琴、钢琴。笛子、埙、小提琴等长按类乐器没有做专门模拟。

目标是快速检查自动演奏脚本是否大致正确，不追求完全复刻游戏音频引擎。
