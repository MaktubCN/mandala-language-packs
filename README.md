# Mandala Language Packs

Mandala 的公开 language 目录。App 内 Market 读取本仓库的 `catalog.json`；无需额外官网或用户上传服务。安装、版本校验与数据格式由 [open-mana](https://github.com/MaktubCN/open-mana) 实现。需要包含 Market 主题/语言包支持的 Mandala 构建；旧版同名 0.1.1 构建不会自动拥有此功能。

## 制作

语言包使用 format=mandala-language、version=1、locale（规范 BCP 47）、name、direction（ltr/rtl）和 messages。messages 的键是界面原始中文，值是译文；必须保留 `{name}` 等占位符。缺失译文回退英文。内置 en、zh-CN 不能覆盖。`messages.en.json` 是当前静态文案参考，可从 open-mana 的 `npx tsx scripts/export-language-template.ts messages.en.json` 更新。动态句子与尚未抽取的少量文案可能不在模板中。

## 提交收录

1. 将纯 JSON 包提交到自己的公开 GitHub 仓库，确认内容授权允许分发，勿提交个人信息、密钥或私有背景图片。也可向本仓库 packages 目录提 PR。
2. 先合入包文件，再取得该文件所在的完整 40 位提交 SHA；不能引用尚未存在的未来提交。
3. 使用 `shasum -a 256 文件.json` 计算原始文件 SHA-256。
4. 提交 PR 修改 `catalog.json`：声明 id、name、description、publisher、version、minAppVersion 和 package 中的 repository/revision/path/sha256。id 使用小写字母、数字和连字符，最多 60 字符；版本使用 x.y.z。
5. 维护者本机校验、审阅后合入。目录收录不代表第三方作者身份或安全的额外背书。

包地址由 repository + 固定 revision + 相对 path 组成；Market 仅访问 GitHub 的公开 HTTPS 端点，不追随任意地址或重定向。单包最多 4 MiB；目录最多 500 项。首版直接分发提交中固定的 JSON 文件，不依赖 GitHub Releases 或运行云端 Actions。

## 更新

提交新包 → 提升 version → 更新固定 revision 和 sha256 → PR 审阅。用户重新浏览条目详情可看到更新按钮；不会后台自动安装。历史版本仍可从 Git 历史取得。没有网络时可管理已经安装的包。


## Arabic starter

`ar.mandala-language.json` 是社区翻译入门包，覆盖主要导航、Market 与部分设置。它不是完整阿拉伯语本地化，也尚未经母语译者审校；界面中其余内容回退英文。欢迎提交翻译补充和 RTL 布局反馈。界面语言不改变 Agent 回答语言或已有对话内容。

示例包和目录采用 MIT 许可；第三方包需在自己的仓库明确许可。
