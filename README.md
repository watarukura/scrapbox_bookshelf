# scrapbox_bookshelf

↓の記事を参考にしました。多謝。
[Scrapboxにて当日の日記用ページを作るPythonスクリプト（当月・前日・翌日へのリンク付き）](http://ich.hatenadiary.com/entry/scrapbox-daily-create)

## scrapboxへ取り込むjsonファイルを作成する
1. booklogにログインし、https://booklog.jp/export にアクセスしてCSVエクスポートする。
2. CSVからISBNリストを取得する
```bash
$ cat booklog20191116233007.csv | awk -F"," 'length($3)==15{print $3}' | pbcopy
```
3. `python src/scrapbox_bookshelf.py`を実行し、scrapbox_import.jsonを作成する
4. scrapboxにログインし、Settings→Page Data→Import Pagesから3.で作成したjsonファイルをimportする