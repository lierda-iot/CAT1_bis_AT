# 在线文档模版

基于 Sphinx 的多语言在线文档模版，支持中英文双语，开箱即用。

## 快速开始

```bash
# 1. 克隆仓库
git clone https://github.com/lierda-iot/CAT1_bis_AT.git my-docs
cd my-docs

# 2. 安装依赖
pip install -r docs/requirements.txt

# 3. 编译文档
cd docs
make build

# 4. 打包部署（生成 dist/ 目录，可直接丢到 nginx）
make dist
```

## 使用说明

### 写文档

文档源文件在 `docs/zh_CN/` 和 `docs/en/` 下，支持 Markdown (.md) 和 reStructuredText (.rst) 两种格式。

每个目录下有一个 `index.rst`，通过 `toctree` 指令引用子页面。新增页面时只需：

1. 在对应目录下创建 `.md` 或 `.rst` 文件
2. 在该目录的 `index.rst` 的 `toctree` 中添加文件名（不带后缀）

### 修改左上角下拉列表（型号切换）

左上角的下拉菜单用于在多个文档站点之间跳转，配置在 `docs/conf_common.py` 的 `_load_model_switcher_config()` 函数中：

```python
def _load_model_switcher_config():
    return {
        "currentModel": "你的项目名",      # 当前站点显示的名称
        "preservePath": False,             # 切换时是否保留当前页面路径
        "models": [
            {
                "name": "项目A",
                "label": "项目A",           # 下拉菜单中显示的文字
                "url": "https://your-domain.com/project-a/zh_CN/index.html",
            },
            {
                "name": "项目B",
                "label": "项目B",
                "url": "https://your-domain.com/project-b/zh_CN/index.html",
            },
        ],
    }
```

如果不需要这个下拉列表，把 `models` 数组清空或只保留一项即可。

### 修改项目名称和版权信息

编辑 `docs/zh_CN/conf.py` 和 `docs/en/conf.py`：

```python
project = "你的项目名称"
copyright = "2024 - {}，你的公司名".format(current_year)
```

### 修改 GitHub 链接

编辑 `docs/conf_common.py` 中的 `html_context`：

```python
html_context = {
    "github_user": "your-username",
    "github_repo": "your-repo",
    "github_version": "main",
    "display_github": True,
}
```

### 替换 Logo

替换 `docs/_static/logo.svg` 为你的项目 Logo。

## 目录结构

```
docs/
├── conf_common.py          # 通用 Sphinx 配置（左上角下拉列表在这里改）
├── Makefile                # 顶层构建入口
├── build_dist.sh           # 部署打包脚本
├── requirements.txt        # Python 依赖
├── _static/                # 静态资源 (CSS/JS/Logo)
├── en/                     # 英文文档
│   ├── conf.py             # 英文项目名/版权
│   └── ...
└── zh_CN/                  # 中文文档
    ├── conf.py             # 中文项目名/版权
    └── ...
```

## 部署

详见 [docs/DEPLOYMENT.md](docs/DEPLOYMENT.md)。
