# FRP Gateway Multi-Manager (TUI版) 🚀

这是一个专为网络工程师和深度折腾玩家设计的 **FRP 服务端多实例图形化管理脚本**。基于 Linux 终端 TUI (Whiptail) 交互和原生 Systemd Template (`@`) 机制构建。

## 💡 为什么写这个项目？

传统的 FRP 穿透通常只有一个 `frps` 进程管理所有设备。当作为主网关节点时，如果把软路由、公司测试服、私人建站服务全混在一起，一旦配置出错或遭到攻击，极易互相牵连。

本脚本实现了**真正的多实例物理隔离**：
- 🏢 **多实例共存**：你可以为 `openwrt` 创建一个跑在 7000 端口的实例，为其他的服务创建跑在 7001 的实例。它们互不干扰，崩溃自动重启。
- 🖥️ **图形化向导**：告别繁琐的 `vi frps.toml`，全程终端 TUI 弹窗点选配置，支持防呆输入。
- 🔒 **安全先行**：内置 TLS 强制加密开关，一键防止云服务商的深度包检测 (DPI)。
- 📝 **日志精准分离**：每个实例的报错信息相互独立，使用 `journalctl` 实时滚动输出。

## 🛠️ 一键安装与使用

支持主流的 Linux 发行版 (Debian / Ubuntu / CentOS)，请确保在 **root** 用户下执行以下一键命令：

```bash
wget -O frps_tui.sh "https://raw.githubusercontent.com/NX2406/frp/refs/heads/main/frps" && chmod +x frps_tui.sh && ./frps_tui.sh
