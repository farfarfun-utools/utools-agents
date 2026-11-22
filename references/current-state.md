# 当前仓库盘点（2026-11-22）

以下是创建/更新 skill 时的状态，不是永久规范。开始任务时重新读取对应仓库。

| 插件 | 实现 | 窗口高度 | Release workflow | 截图 workflow | packages 页面 |
| --- | --- | ---: | :---: | :---: | :---: |
| FunCalc | Vue/Vite | 620 | 有 | 无，CI 有 Playwright 截图 | 有 |
| FunCalendar | Vue/Vite | 620 | 有 | 有 | 有 |
| FunChat | Vue/Vite | 660 | 有 | 有 | 有 |
| FunDoc | Vue/Vite | 600 | 有 | 有 | 有 |
| FunImage | Vite/原生 JS | 720 | 有 | 有 | 有 |
| FunJSON | Vue/Vite | 720 | 有 | 有 | 待注册发版后补充 |
| FunLink | Vue/Vite | 558 | 有 | 有 | 有 |
| FunOTP | Vue/Vite | 558 | 有 | 有 | 有 |
| FunQR | Vue/Vite | 720 | 有 | 有 | 有 |
| FunVideo | Vite/原生 JS | 720 | 有 | 有 | 有 |

10 个仓库的 `utools/logo.png` 都是 256×256 PNG，`plugin.json#main` 都指向 `dist/index.html`；`package.json` 与 `utools/plugin.json` 当前版本一致。10 个插件已进入 `utools-plugins` 和组织 profile，其中 9 个已发布插件已进入 `farfarfun/packages`。`utools-shots` 维护部分 Vue 插件的共享截图脚本，FunImage/FunVideo 使用组织 `.github` 的截图脚本。`utools-mobile` 是内置 FunOTP 与 FunLink 视图的 Android 伴侣应用（通过 `src/shared/` 复用两者的纯业务模块）。`utools-dev` 作为本地聚合工作区通过 `repos.json` 与 `scripts/ws.mjs` 统一管理上述仓库的同步与跨仓巡检。`utools-plugins` 是索引仓库，组织 `.github` 管主页与共享截图工作流，`farfarfun/packages` 管产品页与 Release 下载索引。
