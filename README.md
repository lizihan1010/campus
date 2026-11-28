# 江财生活台 · iPhone 应用

面向江西财经大学学生的校园生活入口。提供手动管理的一周课表、可只选日期或指定时间的待办、课前提醒与灵动岛实时活动、群通知整理、常用校园服务入口以及本地数据备份。**当前为精简版**：清掉多次迭代后失效的旧路径，首页常用入口只保留喝水 / 运动 / 洗澡，课表界面沿用原版 7 列卡片。第三方服务仍由其原应用或页面完成登录、签到和支付；本应用不会代替它们操作账号。

## 下载并安装到 iPhone

1. 打开仓库 **Actions → Build iPhone IPA**，选择**最近一次成功**的运行，在页面底部 **Artifacts** 下载 **CampusLife-unsigned-IPA**。不要下载早期运行留下的旧包。
2. 解压下载的 ZIP，得到 **CampusLife-unsigned.ipa**。这个 IPA 尚未签名，不能直接在 iPhone 上点开安装。
3. 在 Windows 上用支持数据传输的线连接 iPhone，解锁并选择“信任此电脑”。确认 iTunes 可以识别手机。
4. 打开 iLoader，等待设备出现；若显示 **No devices found**，检查数据线、USB 接口、iTunes 驱动和手机的信任提示，然后点 **Refresh**。
5. 在 iLoader 中按提示登录自己的 Apple 账号，选中手机，点 **Import IPA**，选择解压得到的 IPA，按提示完成签名和安装。不要把 Apple ID 密码、验证码或签名证书上传到这个仓库。
6. 如系统要求，在 iPhone **设置 → 隐私与安全性 → 开发者模式** 中启用并重启。打开应用后先添加一门课和一个测试提醒。

免费 Apple 账号的个人开发签名通常需要约每 7 天重新签名。更新或重装前，请先在应用“我的”中导出 JSON 备份。

## 源码与构建

- [完整 SwiftUI 源码包](CampusLife-source.zip)：解压后可找到 `project.yml`、应用源码、灵动岛 Widget Extension 源码与详细说明。使用 XcodeGen 生成 Xcode 工程。
- [GitHub Actions 工作流](.github/workflows/build-ios.yml)：在 macOS 上编译并产出未签名 IPA。修改源码包后推送到仓库会自动重新构建，也可在 Actions 中手动运行。
- 构建是否通过以 Actions 最新一次运行为准；真机上的通知、灵动岛、第三方应用跳转和签到流程仍需在你自己的 iPhone 上验证。
- 本版新增 `CampusLiveActivity` 扩展。若个人签名工具不重签嵌套的 `.appex`，实时活动可能不显示，其余功能不受影响；详见包内 README。
- 升级前请先在应用「我的」导出 JSON 备份：新增了课程提醒与待办重复规则字段，属于 SwiftData 轻量迁移。

本仓库为公开仓库。不要在其中提交课表、群消息、账号资料、备份文件或其他个人数据。
