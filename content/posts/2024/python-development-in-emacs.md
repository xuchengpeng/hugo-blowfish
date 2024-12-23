---
title: "Emacs中Python开发"
date: "2024-12-19"
categories: ["Emacs", "Python"]
tags: ["Eglot", "Pyright", "LSP"]
---

## 创建虚拟环境

```bash
cd /path/to/project
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## 安装LSP服务端

> [Pyright](https://github.com/microsoft/pyright) is a full-featured, standards-based static type checker for Python. It is designed for high performance and can be used with large Python source bases.

```bash
npm install -g pyright
```

## 项目配置

安装完Pyright后，在`pyproject.toml`中增加配置：

```toml
[tool.pyright]
venvPath = "."
venv = ".venv"

[tool.black]
line-length = 120
```

## python-mode配置

在Emacs中使用[Eglot](https://www.gnu.org/software/emacs/manual/html_node/eglot/)作为LSP客户端，在`.dir-locals.el`中增加配置：

```elisp
((python-base-mode . ((python-indent-offset . 4)
                      (python-indent-guess-indent-offset-verbose . nil)
                      (python-shell-interpreter . "python")
                      (python-shell-virtualenv-root . "/path/to/project/.venv/"))))
```

