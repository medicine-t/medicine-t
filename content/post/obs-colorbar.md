---
title: "Obs-Colorbar"
description: ""
date: "2024-02-24T11:04:08+09:00"
thumbnail: ""
categories:
  - ["blog", "tech"]
tags:
  - "obs"
---

放送停止中だったり、映像の試験に使うカラーバー、OBS で出す方法のメモ

<!--more-->

OBS はメディアソースの中で ffmpeg が叩ける

メディアソースのローカルファイルのチェックを外し、入力とファイルフォーマットを指定することで、カラーバーとかを出すことができる

それっぽいカラーバーは、`smptehdbars`とかがあった。
ピー音も出せるらしい。`frequency`だったかな？

![設定](/medicine-t/images/obs-colorbar/settings-colorbar.png)
