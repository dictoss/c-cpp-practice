
# PRACTICE for C

- 参考資料
    - https://ja.wikipedia.org/wiki/C言語
    - https://ja.wikipedia.org/wiki/ANSI_C
    - https://ja.wikipedia.org/wiki/キーワード_(C言語)
    - https://ja.wikipedia.org/wiki/C99
    - https://ja.wikipedia.org/wiki/C11_(C言語)

## C言語の規格

### K&R

- ひとまず置いておく。

### C89

- 概要
    - 規格策定時期が1989年のためとても古い規格がANSIとしての初めての規格
    - Cコンパイラはほぼこの規格に対応していると思われる
- 言語仕様のメモ
    - "//" のコメント記法は（規格上は）使えない。ただ、コンパイラによってはC++の規格をバックポートして使えるようにしている場合がある。
    - 関数プロトタイプの導入
    - void型、enum型の導入
    - 変数の宣言をブロックの最初で行う必要がある
    - const キーワードの導入
    - volatile キーワードの導入

### C99

- 概要
    - 1999年にC89をベースに改訂した新しいC言語の規格
    - C++の規格の一部を取り込んだ
- 言語仕様のメモ
    - 変数の宣言をブロックの最初でなく、途中でも宣言してもよくなった
    - インライン関数のサポート
    - "//" によるコメント記法のサポート
    - 新しい型の追加
        - long long int (組み込み型)
        - _Bool (stdbool.hにて定義。false = 0、true = 1の実装が多いか？)
        - _Complex (complex.hにて定義)
        - _Imaginary (complex.hにて定義)
    - restrict キーワードの追加
        - const、volatileのような感じで指定して使うもの（らしい
        - ポインタ型変数のみに指定できる
        - コンパイラの最適化を助けるもの（らしい）
    - stdint.h、tgmath.h、fenv.h, complex.h のヘッダの追加
        - stdint.h
        - tgmath.h
        - fenv.h
        - complex.h
    - 型宣言がない関数の返り値や変数をint型と自動判定する仕様を廃止
    - 可変長マクロのサポート
    - 指示初期化子
        - 配列などの初期値を初期化時に指定できる
        - ex) int a[] = { [9] = 0 };
            - （要確認）、上記の場合、a[]の要素数は10個らしい。
- C89とC99の違い
    - 関数や変数で型宣言していない場合に暗黙的にint型とみなす仕様がなくなった
        - コンパイルエラーになるんじゃなかろうか
- C99に対応しているかの判定
    - #if __STDC_VERSION__ >= 199901L


### C11

- 概要
    - 2011年に策定されたC99の後継規格
    - 策定途中は"C1X"という書き方をされていた

- 言語仕様のメモ
    - アライメントの仕様
        - _Alignas指定子
        - alignof演算子
        - aligned_alloc関数
        - <stdalign.h>ヘッダファイルの追加
        - C99とC11の違い
    - _Noreturn関数指定子と<stdnoreturn.h>ヘッダファイル。
    - _Genericキーワードを使用した型ジェネリック式
    - マルチスレッドのサポート
        - _Atomic型修飾子 (<stdatomic.h>)
        - _Thread_localストレージクラス指定子
        - <threads.h>ヘッダ
    - unicodeを表現
        - <uchar.h>ヘッダ追加
        - char16_tとchar32_t型
        - u、U、u8リテラル接頭辞の追加
    - gets()廃止
        - gets_s()を使うように変更
    - 無名構造体、無名共用体のサポート
    - 静的アサーション
        - 【調べる】
    - fopen()のオープンモードで"x"の追加（排他オープンで使うO_CREAT|O_EXCLの用に振る舞う）
    - quick_exit()の追加
        - 【調べる】
- C11とC17の違い
    - 【調査中】
- C11に対応しているかの判定
    - #if __STDC_VERSION__ >= 201112L
    - agccではgcc-4.6から利用可能
    - clangではclang-3.1からサポート
    - MSVCでは「Visual Studio バージョン 16.8 以降が必要です」
        - https://docs.microsoft.com/ja-jp/cpp/overview/visual-cpp-language-conformance?view=vs-2019
        - Visual Studio 2019のアップデート版の16.8からサポートしている

### C17

- 概要

- 言語仕様のメモ

- C11とC17の違い

- C17に対応しているかの判定
