# mlreplace
複数ファイルテキスト置換ツール（複数行対応、正規表現対応、事前プレビュー、Ruby）

* 置換前にdiffをとってプレビュー可能
* 複数行対応
* 正規表現対応
* 置換対象ファイルの改行コード自動判別
* ファイルが指定されない場合は、カレントディレクトリ以下の全ファイルを対象

## 使用例

引数なしで起動するとエディタが起動するので、検索文字列と置換文字列を入力します。
ファイルを保存してエディタを終了すると、カレントディレクトリ以下の全ファイルを対象に置換を行います。
現在、バックアップ機能は無効になっています。

```
# mlreplace
From = [path]
To   = [mogemoge
]
--- asd 2015-07-12 18:57:30.039999998 +0900
+++ asd.tmp     2015-08-14 02:44:39.069999998 +0900
@@ -1,5 +1,7 @@
 var fs = require('fs');
-var path = require('path');
+var mogemoge
+ = require('mogemoge
+');
 
 var walk = function(dir, process_file, done) {
        var results = [];
@@ -12,7 +14,8 @@
                        return done(null, results);
                }
                list.forEach(function(file) {
-                       file = path.resolve(dir, file);
+                       file = mogemoge
+.resolve(dir, file);
                        fs.stat(file, function(err, stat) {
                                var info = process_file(file, stat);
                                if (info != null) {
置換を実行してよろしいですか？(Y/n/q/a) 
Changed: asd
1 個のファイルを置換しました。
```

## オプション
```
$ ./mlreplace -h                                                                                               [master]
Usage: mlreplace [options] [files...]
テキストファイル置換ツール
・置換前にdiffをとってプレビュー可能
・.bakつきでバックアップをとります
・複数行対応
・正規表現対応
・置換対象ファイルの改行コード自動判別
・ファイルが指定されない場合は、カレントディレクトリ以下の全ファイルを対象
    -a, --argument                   置換文字列を引数から取得します。
    -c, --clean                      バックアップファイルを削除します。
    -d, --diff                       各ファイルを置換する前にdiffを表示し、確認を求めます。
    -r, --revert                     バックアップファイルを元のファイルに戻します。
    -e, --euc                        置換対象ファイルがEUC-JPであると仮定します。
    -j, --jis                        置換対象ファイルがISO-2022-JPであると仮定します。
    -s, --sjis                       置換対象ファイルがShift_JISであると仮定します。
    -f, --file=FILE                  置換対象ファイル名をファイルから取得します（1行に1個）。
```
