# super-agent 安装指南

本仓库是 DeepSeek Super-agent 研究原型的沙盒测试仓库，只包含文档，不用于生产环境。下面按环境、依赖、安装、验证、排错五节说明本地准备流程，每节给出约 200 字说明和一条可直接执行的命令。

## 环境

推荐使用 64 位 Linux 或 macOS；Windows 建议先安装 WSL2 和 Ubuntu 发行版，再在 WSL 终端中操作，避免路径分隔符和换行符带来的差异。需要 Git 2.30 及以上版本，用于克隆仓库和查看提交记录；需要 Node.js 22.19 及以上版本，它自带 Corepack，因此不必单独安装 pnpm。如果系统尚未安装 Node.js，请从官网下载 22.19 以上的 LTS 版本并按默认选项安装。安装前请确认网络能够访问 GitHub，并预留至少 100 MB 磁盘空间存放仓库和文档；若 Git 版本过低，请通过系统包管理器升级后再克隆。如果只是阅读文档，无需配置其他开发工具。运行以下命令检查 Node.js 版本，输出 `v22.19.0` 或更高版本即符合要求；若版本偏低，请先升级 Node.js 再继续：

```bash
node --version
```

## 依赖

当前仓库没有 `package.json`、锁文件或第三方运行时依赖，克隆后无需执行 `npm install` 或 `pnpm install`，也没有编译、构建步骤。唯一的依赖工具是 Node.js 自带的 Corepack，它负责提供 pnpm 命令，因此不必全局安装 pnpm，也不需要其他全局工具。首次启用后，Corepack 会在 Node.js 的 bin 目录生成 pnpm 的命令垫片；首次执行 pnpm 时可能需要联网下载对应版本，若网络受限，可以先配置 npm registry 镜像再重试。如果系统提示找不到 corepack，说明 Node.js 安装不完整，重新安装 Node.js 即可。如果后续仓库正式引入依赖，再在根目录执行 `pnpm install` 安装即可。由于没有依赖文件，Corepack 只需要启用一次，之后 pnpm 命令会一直可用。启用 Corepack 的命令如下：

```bash
corepack enable
```

## 安装

安装只是把仓库克隆到本地：先切换到准备存放项目的目录，再执行下面的命令。命令会创建 `super-agent` 目录并进入其中，不会下载依赖或执行构建，过程通常只需几秒。仓库体积很小，直接完整克隆即可，不需要使用浅克隆参数。完成后当前目录应包含 `README.md` 和 `docs/`。如果目标目录已存在，请更换存放路径或先清理旧目录，避免克隆失败。本仓库为文档仓库，不需要启动服务、配置数据库或修改系统环境变量，直接用编辑器阅读或修改 Markdown 即可。命令使用 HTTPS 协议，无需事先配置 SSH 密钥；若已配置 SSH，也可以改用 SSH 地址。克隆并进入仓库：

```bash
git clone https://github.com/likangda6/super-agent.git && cd super-agent
```

## 验证

克隆完成后确认工具链和文件都正常。下面的命令会输出 pnpm 版本，检查 `docs/a-install.md` 是否存在，并在两项都通过时打印“安装成功”。pnpm 能输出版本号，说明 Node.js 与 Corepack 配置正确；文件检查通过，说明仓库内容完整。若命令返回非零状态码，请回到前面的步骤检查 Node.js 版本和克隆结果，也可以单独执行 `pnpm --version` 或 `ls docs` 定位问题。该检查不会修改仓库内容，可以重复执行；如果终端提示找不到 test 命令，说明当前不是 Linux、macOS 或 WSL2 环境，请切换后再试。如果只想浏览文档，完成上面的检查即可，不需要启动任何服务。两项都通过后即可开始阅读或编辑文档。验证安装结果：

```bash
pnpm --version && test -f docs/a-install.md && echo "安装成功"
```

## 排错

遇到问题先确认 Node.js 不低于 22.19，并重新执行 `corepack enable`。若提示 `pnpm: command not found`，多为 Corepack 未启用或 PATH 未包含 Node.js 的 bin 目录；若 `corepack enable` 报 EACCES，可先创建目录，再用 `--install-directory ~/.local/bin` 指定安装位置，并把该目录加入 PATH；不要用 sudo 覆盖系统目录，安装到用户目录更安全。若 `git clone` 超时或返回 403，请检查网络与代理，必要时设置 `http.proxy` 后重试，也可以先确认浏览器能否打开 GitHub，以判断是否为网络问题。若命令在 Windows 原生终端无法执行，请改用 WSL2。请先在仓库根目录执行命令，路径错误也会导致检查失败。若仍无法解决，请把命令输出和操作系统版本提供给维护者。下面的命令可一次收集三个工具的版本信息，便于定位问题：

```bash
node --version && corepack --version && git --version
```
