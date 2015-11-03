# ocaml-jikken

http://logic.cs.tsukuba.ac.jp/jikken/ に従ってミニOCamlインタープリタを作る実験です。同サイト上で配布されているファイルを同梱しています。

インタープリタ部分はカリキュラムに従ってeval.mlというファイルに書いていってください。

## 使い方

eval.mlがある状態でmakeと打つと、miniocamlというコマンドができる。

[miniocamlコマンドの説明](http://logic.cs.tsukuba.ac.jp/jikken/parse.html)

> 上記のように、たくさんのファイルを毎回 OCamlから読みこむのは大変なので、 「上記のファイルすべてを読み込み済みの OCaml処理系」を作る方法 が Makefile に書かれている。 ここでは eval.ml というファイルに、インタープリタ本体が格納されていると仮定している。 Makefile を使いたいときは、Unix シェルから単に make とすれば良い。 そうすると、miniocaml というコマンドができる。

main.mlにコマンドの使い方が書いてある。

>
使用例は以下の通り。parse関数は Mainモジュールにはいっているので
>
    open Main;; parse "...";; とするか Main.parse "...";;
>
として呼びだす。
>
    $ ./miniocaml
          Objective Caml version 3.09.1
>
    # Main.parse "let x = 3 + 1 * 4 in fun y -> x + y";;
    - : Syntax.exp =
    Syntax.Let ("x",
     Syntax.Plus (Syntax.IntLit 3,
      Syntax.Times (Syntax.IntLit 1, Syntax.IntLit 4)),
     Syntax.Fun ("y", Syntax.Plus (Syntax.Var "x", Syntax.Var "y")))
    #  Main.parse "1 + 2 * 3 ";;
    - : Syntax.exp =
    Syntax.Plus (Syntax.IntLit 1,
     Syntax.Times (Syntax.IntLit 2, Syntax.IntLit 3))
    #
