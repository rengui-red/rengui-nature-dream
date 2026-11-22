\# 🌿 仁归 · 开发手册



> 面向开发者与贡献者的技术指南



\---



\## 一、技术栈概览



| 层次 | 技术 | 说明 |

|------|------|------|

| 视图层 | HTML5 + CSS3 | 语义化标签，响应式设计 |

| 逻辑层 | Vanilla JavaScript (ES6+) | 零框架，模块化 IIFE |

| 数据层 | localStorage | 键前缀 `rengui\_` |

| AI层 | 规则引擎 | 关键词匹配 + 模板回应 |

| 音频层 | Web Audio API | 实时合成，无需音频文件 |

| 绘画层 | Canvas API | 自由涂鸦与游戏 |

| 后端（可选） | Python Flask | 仅用于数据同步 |



\---



\## 二、命名规范



\### 文件命名

\- HTML 页面：`kebab-case.html`（如 `rain-heart.html`）

\- JS 模块：`kebab-case.js`（如 `ai-core.js`）

\- 游戏模块：`game-name.js`（如 `ripple-game.js`）



\### 代码命名

\- 全局命名空间：`RenguiXXX`（如 `RenguiUtils`、`RenguiAI`）

\- 类名：`PascalCase`（如 `RainMixer`）

\- 方法名：`camelCase`（如 `addStone`）

\- 常量：`UPPER\_SNAKE\_CASE`（如 `STORAGE\_PREFIX`）

\- 私有方法：以下划线开头（如 `\_containsAny`）



\### 存储键命名

\- 前缀：`rengui\_`

\- 短横线分隔：`rengui\_diary\_entries`

\- 定义在 `global-config.js` 的 `STORAGE\_KEYS` 中



\---



\## 三、模块架构



\### 核心模块（`src/js/core/`）



| 模块 | 职责 | 全局对象 |

|------|------|---------|

| `global-config.js` | 全局配置、版本号、存储键 | `RenguiConfig` |

| `utils.js` | 工具函数、转义、toast | `RenguiUtils` |

| `storage.js` | localStorage 封装 | `RenguiStorage` |

| `culture-data.js` | 文化内容库（诗词、星宿） | `RenguiCulture` |

| `ai-core.js` | AI情感分析与回应 | `RenguiAI` |

| `audio-engine.js` | 音频合成与混音 | `RenguiAudio` |

| `mental-scale.js` | 心理测评量表定义 | `RenguiMentalScale` |



\### 游戏模块（`src/js/games/`）



| 游戏 | 类名 | 所属页面 |

|------|------|---------|

| 涟漪散忧 | `RenguiRippleGame` | rain-heart.html |

| 雨窗涂鸦 | `RenguiFogDoodle` | rain-heart.html |

| 雨巷寻伞 | `RenguiUmbrellaHunt` | rain-heart.html |

| 雨声调音台 | `RenguiRainMixer` | rain-heart.html |

| 摘星成诗 | `RenguiStarCatcher` | star-wish.html |

| 星愿花园 | `RenguiStarGarden` | star-wish.html |

| 星宿漫游 | `RenguiConstellationMap` | star-wish.html |

| 流星祈愿 | `RenguiMeteorWish` | star-wish.html |

| 呼吸圈 | `RenguiBreathCircle` | relax-game.html |

| 释忧气球 | `RenguiWorryBalloon` | relax-game.html |



\---



\## 四、安全约束



1\. \*\*所有用户输入必须转义\*\*：使用 `RenguiUtils.escapeHtml()`

2\. \*\*禁止使用 `innerHTML` 渲染用户内容\*\*（除非已转义）

3\. \*\*禁止引入外部脚本\*\*：所有代码必须本地运行

4\. \*\*禁止发送网络请求\*\*：核心功能不得依赖网络

5\. \*\*存储数据大小限制\*\*：单个画作不超过 2MB，避免 localStorage 溢出



\---



\## 五、版本策略



遵循语义化版本 `MAJOR.MINOR.PATCH`：



\- \*\*MAJOR\*\*：架构级变更，不兼容旧版

\- \*\*MINOR\*\*：新增功能或模块

\- \*\*PATCH\*\*：Bug 修复



当前版本：\*\*2.0.0\*\*



\---



\## 六、贡献流程



1\. Fork 项目

2\. 创建分支：`git checkout -b feature/your-feature`

3\. 提交更改：`git commit -m 'feat: add something'`

4\. 推送分支：`git push origin feature/your-feature`

5\. 提交 Pull Request



\### 提交规范


feat: 新增功能
fix: 修复Bug
docs: 文档更新
style: 样式调整
refactor: 代码重构
test: 测试相关

text

---

## 七、扩展指南

### 新增心理测评量表

1. 在 `mental-scale.js` 中添加量表定义
2. 在 `global-config.js` 的 `STORAGE_KEYS` 中添加存储键
3. 创建对应的对话式页面或复用现有页面

### 新增游戏

1. 在 `src/js/games/` 创建游戏文件
2. 定义类并挂载到全局（如 `global.YourGame = YourGame`）
3. 在页面逻辑中引入并初始化

### 扩展AI关键词

在 `ai-core.js` 的 `emotionKeywords` 对象中添加关键词，并在 `generalResponses` 中补充回应模板。

---

## 八、性能注意事项

- Canvas 动画使用 `requestAnimationFrame`
- 粒子数量控制在合理范围（≤200）
- localStorage 写入前检查数据大小
- 移动端降低动画帧率或粒子数量











