+++
author = "satou yuuki"
title = "気合いで読むthe art of readable code"
date = "2022-05-17"
description = "気合いで読むthe art of readable code"
tags = [
    "readable code",
]
+++

# なぜ本を読むのか
プログラミングの命名について指摘されることが増えた。英語のリーディングの練習

# 本のタイトル
readable code
[PDFリンク](https://mcusoft.files.wordpress.com/2015/04/the-art-of-readable-code.pdf)

- 広い意味の動詞をなるべく使わない
```
bad: GetPage() // どこから取得するのかわからない
good: FetchPage(), DownloadPage() // インターネットから取ってくる
```

- 意味のない変数名を避けて意味のある変数名にしよう
```
bad: retval(意味: return value)
good: sum_square(意味: 平方根の合計)
```

- ループで使う変数もわかりやすく命名しよう
```
bad: i, j, k
good: clubs-> ci, members-> mi, users->ui
```

- 変数名はdirect, explicitな意味を使う
```
bad: --run_locally
good: --extra_logging
```

## 格言: 変数名は小さなコメントのようなものだ

- 変数に含められる情報ならコメントではなく変数名に含める
```
bad: string id; // Example: "af84ef845cd8"
good: hex_id
```

- 変数名に情報を含めるとバグを見つけやすい
```
bad: var start = (new Date()).getTime();
good: var start_ms = (new Date()).getTime();  //返り値がmillisecondsだということが明らかになる
```

- Q. 変数の長さは結局どのぐらいの長さにすればいいのか
- A. 変数のスコープが狭ければ短い名前でも良い。グローバルで使われる変数ほど詳細度をあげる。
※長いと打ち込むのが疲れるからは長い変数名を避ける理由にならない(エディターが候補を出してくれるから)

- 新しいチームメイトがすぐ理解できないような命名なら使わない
```
bad: BEManagement
good: BackEndManagement
```
