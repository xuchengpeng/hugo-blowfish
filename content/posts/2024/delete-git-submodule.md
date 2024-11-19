---
title: "删除Git Submodule"
date: "2024-11-19"
categories: ["Linux"]
tags: ["Git"]
---

1. 删除子模块目录；
2. 删除`.gitmodules`中对应的子模块内容；
3. 删除`.git/config`中对应的子模块内容；
4. 删除`.git/modules/`下对应的子模块目录；
5. `git rm --cached 子模块目录`。
