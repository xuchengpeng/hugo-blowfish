---
title: "Iosevka with IBM Plex Mono style"
date: "2025-04-16"
categories: ["Computer Science"]
---

[Iosevka](https://github.com/be5invis/Iosevka) [ˌjɔˈseβ.kʰa] is an *open-source, sans-serif + slab-serif, monospace + quasi‑proportional* typeface family, designed for *writing code*, using in *terminals*, and preparing *technical documents*.

Iosevka支持多种风格设置，并且很方便进行自定义构建。这里介绍下如何继承[IBM Plex Mono](https://github.com/IBM/plex)字体风格，并修改字宽、连字符、个别字符风格。

首先需要安装[nodejs](http://nodejs.org/)(≥18.0.0)和[ttfautohint](http://www.freetype.org/ttfautohint/)。下载Iosevka仓库后，安装相关包文件。

```shell
git clone --depth=1 https://github.com/be5invis/Iosevka.git
cd Iosevka
npm install
```

可以在[Iosevka Customizer](https://typeof.net/Iosevka/customizer)进行自定义风格设置，生成的配置文件保存在 `private-build-plans.toml` 中。

```toml
[buildPlans.IosevkaPlex]
family = "Iosevka Plex"
spacing = "normal"
serifs = "sans"
noCvSs = true
exportGlyphNames = false
noLigation = true

[buildPlans.IosevkaPlex.variants]
inherits = "ss15"

[buildPlans.IosevkaPlex.variants.design]
zero = "slashed"

[buildPlans.IosevkaPlex.widths.Normal]
shape = 600
menu = 5
css = "normal"
```

执行 `npm run build -- contents::IosevkaPlex` 构建TTF和Web Font。

执行 `npm run build -- ttf::IosevkaPlex` 只构建TTF。默认情况下，构建会根据系统的CPU线程数启动多个并发任务，可能会导致CPU被全部占用，或者是内存不足导致OOM，通过执行 `npm run build -- --jCmd=2 ttf::IosevkaPlex` 来指定并发任务数目。

构建完成后，字体文件保存在 `dist` 目录下。
