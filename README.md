# sculk-demo

基于 [sculk](https://github.com/KercyDing/sculk) P2P 隧道库的 GUI 演示程序，使用 [egui](https://github.com/emilk/egui) 构建。

## 功能

- **建房**：暴露本地 Minecraft 服务端，生成可分享的 `sculk://...` 票据
- **加入**：通过票据连接到房主隧道，转发流量到本地端口
- 跨重启的配置与密钥持久化

## 环境依赖

### Rust

需要 Rust 1.89+：

```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

### Linux 系统库

```sh
# Debian / Ubuntu
sudo apt-get install \
  libxkbcommon-dev \
  libwayland-dev \
  libgl1-mesa-dev \
  libglib2.0-dev

# Fedora / RHEL
sudo dnf install \
  libxkbcommon-devel \
  wayland-devel \
  mesa-libGL-devel \
  glib2-devel
```

## 构建

```sh
cargo build --release
```

Windows 产物为 `target/release/sculk-demo.exe`，可直接双击运行。

## 打包

### macOS（`.app`）

使用 [cargo-bundle](https://github.com/burtonageo/cargo-bundle)：

```sh
cargo install cargo-bundle
cargo bundle --release
```

产物路径：`target/release/bundle/osx/sculk demo.app`

### Linux RPM（`.rpm`）

使用 [cargo-generate-rpm](https://github.com/cat-in-136/cargo-generate-rpm)：

```sh
cargo install cargo-generate-rpm
cargo build --release
cargo generate-rpm
```

产物路径：`target/generate-rpm/sculk-demo-*.rpm`

### Linux DEB（`.deb`）

使用 [cargo-deb](https://github.com/kornelski/cargo-deb)：

```sh
cargo install cargo-deb
cargo deb
```

产物路径：`target/debian/sculk-demo_*.deb`

## 使用

1. **建房**：填写 MC 端口、可选密码和最大人数 → 点击 **Start Host** → 分享票据
2. **加入**：粘贴票据，填写本地端口和密码 → 点击 **Join**

日志显示在底部面板，票据可通过 **Copy to Clipboard** 按钮复制。

## 许可证

[GPL-3.0](LICENSE)
