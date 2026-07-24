\# 🌿 仁归·自然之梦 — Git 推送上线指南


> \*\*目标\*\*：将项目安全、完整、合规地推送至 GitHub 公开仓库，供社区使用与协作。


\---


\## 一、推送前必须完成的安全审查


\### 1. 确认敏感文件已被忽略

检查根目录 `.gitignore` 是否包含以下内容：


数据库文件（包含用户数据，绝对不能提交）


\*.db

\*.sqlite3

\*.sqlite


环境配置文件（包含密钥）


.env


Python 缓存

pycache/

\*.pyc

\*.pyo


系统文件


.DS\_Store

Thumbs.db


备份与临时文件

backup/

temp/


编辑器配置（可选）

.vscode/

.idea/


\### 2. 检查代码中是否残留任何硬编码密钥

在项目根目录执行搜索（或手动检查）：

\- 搜索 `SECRET\_KEY`、`password`、`api\_key` 等关键字。

\- 确保 `config.py` 中 `SECRET\_KEY` 使用的是环境变量或默认开发值，并已添加注释说明。


\### 3. 确认数据库文件不存在

\- 检查 `src/database/` 目录下是否存在 `rengui\_data.db`。

\- \*\*如果存在，必须删除\*\*。该文件是运行时生成，包含本地用户数据。

\- 保留 `.gitkeep` 文件确保目录被追踪即可。


\### 4. 确认所有用户数据已清除

\- 删除浏览器 `localStorage`、`indexedDB` 中测试遗留数据（仅影响本地调试，不影响 Git 仓库）。


\---


\## 二、推送前的准备工作


\### 1. 完善 `LICENSE` 文件

\- 确保根目录存在 `LICENSE` 文件，内容为 MIT 许可证全文。

\- 如果尚未创建，请复制标准 MIT 协议文本。


\### 2. 完善 `README.md`

\- 确认项目介绍、快速开始、隐私声明、技术栈等描述准确。

\- 将 GitHub 仓库地址更新为实际地址：https://github.com/rengui-red/rengui-nature-dream


\### 3. 确认文档文件完整

检查 `docs/` 目录下的四个文件是否就绪：

\- `manifest.md`

\- `privacy.html`

\- `dev-manual.md`

\- `update-log.md`


\### 4. 统一代码风格（可选）

\- 确保所有文件使用 UTF-8 编码。

\- 确保 HTML 文件无破坏性语法错误。


\---


\## 三、推送次序（从本地到 GitHub）


\### 1. 初始化本地 Git 仓库（如果尚未初始化）

```bash

cd rengui-nature-dream

git init


2\. 添加所有文件到暂存区

bash

git add .


3\. 检查将要提交的文件列表

bash

git status

重点确认：列表中没有 .db、.env、\_\_pycache\_\_ 等敏感文件。


4\. 进行首次提交

bash

git commit -m "🌿 初始提交：仁归·自然之梦 v1.0.0"


5\. 关联远程仓库

在 GitHub 上创建一个公开仓库（不要勾选“Initialize this repository with a README”），然后执行：


bash

git remote add origin https://github.com/你的用户名/rengui-nature-dream.git


6\. 推送到远程

bash

git branch -M main

git push -u origin main


四、推送后的验证


访问 GitHub 仓库页面，确认所有文件已正确显示。


检查 src/database/ 目录下只有 .gitkeep，没有数据库文件。


检查 README.md 能正常渲染，链接可点击。


尝试在另一台设备上克隆仓库并启动项目，验证流程完整性。


五、法律与责任声明


1\. 许可证

本项目采用 MIT 许可证。任何人可自由使用、修改、分发，但必须保留原始版权声明。原作者不对软件的使用后果承担任何责任。


2\. 免责声明

本项目是一个本地运行的心理健康工具，不提供任何在线医疗服务。使用者应自行承担使用风险。如果感到严重的心理困扰，请寻求专业医疗帮助。


3\. 隐私承诺

本项目不收集、不存储、不上传任何用户数据。所有数据仅存在于使用者本地设备。使用者应自行保护自己的本地数据安全。


六、风险提示与应对


风险	说明	应对措施

代码被恶意修改后分发	MIT 协议允许修改，坏人可能植入恶意代码后二次分发	在 README 中提醒用户从官方 GitHub 仓库下载，并校验文件哈希

用户将本地服务暴露到公网	可能导致未授权访问	在文档中明确警告“请勿将服务监听在 0.0.0.0”，默认使用 127.0.0.1

依赖库漏洞	Flask 等依赖未来可能发现安全漏洞	定期检查并更新 requirements.txt，启用 GitHub Dependabot

商标被冒用	“仁归”品牌可能被他人用于商业行为	可在 README 中声明“仁归”为项目名称，建议社区尊重但不强制法律约束


七、维护建议


&#x20; 1，开启 GitHub Discussions：作为社区交流渠道。


&#x20; 2，设置 Issue 模板：引导用户规范提交 Bug 或建议。


&#x20; 3，添加 SECURITY.md：提供安全漏洞报告方式（推荐启用 GitHub 安全通告功能）。


&#x20; 4，定期备份：将仓库镜像到 Gitee 或本地硬盘。





