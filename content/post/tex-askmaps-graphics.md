---
title: "TexでAskmapsとgraphicsでハマった話"
date: 2023-05-29T14:45:36+09:00
draft: false
tags: ["tex"]
categories: ["blog"]
---

カルノー図を書きたくて askmaps パッケージを、図を入れたくて graphics を使っていたらなんか図が表示されない…とくにログも出てない…

結論としては graphics より先に askmaps を読み込んだら図が表示された。

```tex
\usepackage{askmaps}
\usepackage[dvipdfmx]{graphicx}
```
