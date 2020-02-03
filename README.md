# shell_memo_to_self

### Shell / Unix チートシート

  https://github.com/miolab/shell_memo_to_self.git


---

## シェル（shファイル）ヘッダーに書くシバン

`#!/bin/sh`

↓ みたいにかく。
```
#!/bin/sh
date >> date.txt
```

## シェル実行（e.g.）

  `$ ./hoge.sh`


# Unixコマンド

## パーミッション管理

```
chmod xxx aaaa.aaa
```


---

## 検索

### __grep__

__文字列__ を、ファイルをひらかずにサーチ。

- 基本形

  `grep some_word aaaa.aaa`

- 文字列の一部だけでもOK

  `grep som aaaa.aaa`

- ワイルドカードも使える。（対象ファイルを決め打ちにしない）

  `grep some_word *`


### __find__

__ファイル__ を検索して、パスを返す。

- 基本形

  `find ディレクトリ名 -name ファイル名 -print`
    ```
    find dir_hoge -name moge.txt -print

    # dir_hoge/moge.txt
    ```

- ワイルドカード併用

  `find dir_hoge -name '*.txt' -print`
  - `"*.txt"` のようにダブルクォーテーションでもOK

- ルートを基点にして検索（findは下部ディレクトリもサーチしてくれる）

  `find ./ -name 'hoge.txt' -print`
  - ルートで実行すると全ディレクトリに対して検索をかけ、検索結果がたいへんなことになるため、スコープをしぼる等の工夫は必要。


---

## リダイレクション

例

- 結果をファイルにする

  `命令文 > ファイル名`
    ```
    grep hoge moge.txt >> kekka.txt
    ```

    - `>>` にすると文末に追加できる。  
      （`>` だと上書き）


---

## 削除

- 空ディレクトリ削除

  `rmdir`

- 強制削除（ディレクトリが中身を持つ場合）　※取り扱い注意

  `rm -r ccc`

