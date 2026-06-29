# fetch_clash_proxies

从 `https://socks5-proxy.github.io/` 抓取免费代理，并生成 Clash 可用的配置文件。

默认输出文件为：`clash-free-proxies.yaml`。

## 快速使用

直接运行：

```bash
python fetch_clash_proxies.py
```

指定输出文件：

```bash
python fetch_clash_proxies.py -o clash.yaml
```

指定代理列表来源：

```bash
python fetch_clash_proxies.py --url https://socks5-proxy.github.io/ -o clash.yaml
```

运行成功后，会在当前目录生成 Clash 配置文件。

## Clash 订阅地址

仓库里的 `clash-free-proxies.yaml` 可以作为 Clash 订阅文件使用。

如果仓库是公开仓库，订阅地址格式为：

```text
https://raw.githubusercontent.com/<用户名>/<仓库名>/main/clash-free-proxies.yaml
```

把 `<用户名>` 和 `<仓库名>` 替换成实际的 GitHub 用户名和仓库名即可。

## 自动更新

项目包含 GitHub Actions workflow：

```text
.github/workflows/update-proxies.yml
```

它会：

- 每天北京时间约 04:00 自动运行一次；
- 也可以在 GitHub Actions 页面手动触发；
- 重新生成 `clash-free-proxies.yaml`；
- 如果文件有变化，则自动提交到 `main` 分支。

如果自动提交失败，请检查仓库设置：

```text
Settings → Actions → General → Workflow permissions → Read and write permissions
```

## 注意事项

- 免费代理的稳定性和可用性无法保证。
- 源站页面结构变化时，脚本可能解析失败。
- 如果仓库是私有仓库，Clash 客户端通常不能直接读取 GitHub raw 地址。
- 生成失败时，GitHub Actions 会保留仓库中已有的上一版 `clash-free-proxies.yaml`。
