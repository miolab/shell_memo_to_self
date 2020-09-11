# Shell and Linux memo

Shell / Linuxコマンド チートシート

---

## シェル（shファイル）ヘッダーに書くシバン

`#!/bin/sh`

↓ みたいに書く。
```shell
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

### grep

__文字列__ を（ファイルをひらかずに）サーチ。

#### 使用例

  ```bash
  asdf list-all elixir | grep 1.10

  1.10.0-rc.0
  1.10.0-rc.0-otp-21
  1.10.0-rc.0-otp-22
  1.10.0
  1.10.0-otp-21
  1.10.0-otp-22
  1.10.1
    .
    .
  ```

  ```bash
  grep any_word any_path/* --include "*.ex"
  ```

  ディレクトリ`any_path`配下の全ファイルのうち、拡張子が`.ex`であるファイルで、  
  かつ、ファイルの中身に文字列`any_word`を含むファイルをリストにして返す。

- 基本形 : `grep 文字列 ファイル名`
  ```
  grep some_word aaaa.aaa
  ```

- 文字列の __一部だけ__ でもOK
  ```
  grep som aaaa.aaa
  ```

- 一応ワイルドカードも使える。（対象ファイルを決め打ちにしない）
  ```
  grep some_word *
  ```


### find

- __ファイル__ を検索

  - 基本形 : `find 検索対象パス -name ファイル名 -print`

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

- __ディレクトリ__ 検索

  `find 検索対象パス -name ディレクトリ名 -type d`

  ```
  sudo find /usr/local/ -name python -type d
  ```

---

## リダイレクション

例

- 結果をファイルにする

  `命令文 > ファイル名`
    ```
    grep hoge moge.txt >> kekka.txt
    ```

    - `>` だと __上書き__
    - `>>` にすると、__文末に追加__ できる

---

## 削除

- 空ディレクトリ削除

  `rmdir`

- 強制削除（ディレクトリが中身を持つ場合）　※取り扱い注意

  `rm -r ccc`


---

## その他

### curl (カール)
- PCローカルへダウンロード
  ```
  curl https://miolabhogehoge.com
  ```
  - `https/httpアクセス`するコマンドであるともとれる。

### `（コマンド文末に）&` と `fg`

- `（コマンド文末に）&` ... バックグラウンドで処理する
- `fg` ... フォアグランド処理に戻す

  例

  ```terminal
  $ sleep 10 &
  [1] 26762

  $ ps
    PID TTY           TIME CMD
    350 ttys000    0:00.02 -bash
      .
      .
  23625 ttys010    0:00.03 -bash
  26762 ttys010    0:00.00 sleep 10

  $ fg
  sleep 10
  ```
