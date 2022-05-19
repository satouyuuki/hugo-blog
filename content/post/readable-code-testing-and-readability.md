+++
author = "satou yuuki"
title = "気合いで読むthe art of readable code part2"
date = "2022-05-19"
description = "気合いで読むthe art of readable code part2"
tags = [
    "readable code",
]
+++

# 本を読む目的
テストコードを書こうと思ったので読んだ

# 本のタイトル
readable code
[PDFリンク](https://mcusoft.files.wordpress.com/2015/04/the-art-of-readable-code.pdf)

# メモ
- テストコードはreadableに書く。他の人が快適に変更を加えられるように。
- テストコードの処理を見やすくするようにhelper functionを追加する
```
bad: 
vector<ScoredDocument> docs;
docs.resize(5);
docs[0].url = "http://example.com";
docs[0].score = 3;
...
good: 
void MakeScoredDoc(ScoredDocument* sd, double score, string url) {
    sd->score = score;
    sd->url = url;
}
voctor<ScoredDocument> docs;
docs.resize(5);
MakeScoredDoc(&docs[0], 3, "http://example.com");
```

- helper functionの機能を使いやすくする
```
まあまあ: 
void MakeScoredDoc(ScoredDocument* sd, double score, string url) {
    sd->score = score;
    sd->url = url;
}
good: 
void AddScoredDoc(vector<ScoredDocument>& docs, double score) {
    ScoredDocument sd;
    sd.score = score;
    sd.url = "http://example.com";
    docs.push_back(sd);
}
vector<ScoredDocument> docs;
AddScoredDoc(docs, 3);
```
- 命名をわかりやすくする
```
good: 
void CheckScoresBeforeAfter(string input, string expected_output) {
    vector<ScoredDocument> docs = ScoredDocsFromString(input);
    SortAndFilterDocs(&docs);
    string output = ScoredDocsToString(docs);
    assert(output == expected_output);
}
```

- assertionエラー文言もわかりやすくする
```
まあまあ: 
assert(output == expected_output);
good:(ex: Boost c++ library)
BOOST_REQUEST_EQUAL(output, expected_output);
```

- ネーミングに規則を持たせる
```
bad: 
Test1() {...}
good:
Test__<FunctionName>_<Situation>() {...}
```