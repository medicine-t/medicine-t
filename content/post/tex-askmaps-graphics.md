---
title: "TexでAskmapsとgraphicsでハマった話"
date: 2023-05-29T14:45:36+09:00
draft: false
tags: ["tex"]
---

カルノー図を書きたくてaskmapsパッケージを、図を入れたくてgraphicsを使っていたらなんか図が表示されない…とくにログも出てない…

結論としてはgraphicsより先にaskmapsを読み込んだら図が表示された。
```tex
\usepackage{askmaps}
\usepackage[dvipdfmx]{graphicx}
```


