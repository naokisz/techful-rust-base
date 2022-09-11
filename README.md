<!-- -*- coding:utf-8-unix -*- -->

# TechFUL Rust Base

[TechFUL](https://techful-programming.com/)でrustの問題を解く時の自分用[cargo-generate](https://crates.io/crates/cargo-generate)テンプレートです。  
[Atcoder Rust Baseのjaブランチ](https://github.com/rust-lang-ja/atcoder-rust-base/tree/ja)を元にして作成しました。


## 使い方

現時点linux環境のみ対応しています。

### 必要なクレートのインストール

* [cargo-generate](https://crates.io/crates/cargo-generate)
* [cargo-equip](https://crates.io/crates/cargo-equip)
* [cargo-make](https://crates.io/crates/cargo-make)

### パッケージの生成

`cargo generate`コマンドでパッケージを生成します。

```console
$ cargo generate --name sample-problem \
    --git https://github.com/naokisz/techful-rust-base \
    --branch main
```

- `--name`: これから作成するパッケージの名前。好きな名前が付けられる。例：`sample-problem`
- `--branch`: このテンプレートリポジトリのブランチ名。


### 解答となるプログラムの作成

1. 使用するクレートの選択
   - デフォルトで[proconio\_for\_1\_39\_0](https://github.com/naokisz/proconio-rs-for-1.39.0)のみを有効化しています。
   - 手元でテストをする場合はdev-dependenciesの中のクレートをアンコメントしてください。

1. 使用するクレートのドキュメントの生成
   - 必須ではありませんが、以下のコマンドで依存クレートのドキュメントをビルドし、Webブラウザで開いておくと便利でしょう。

      ```console
      $ cargo doc --open   # ドキュメントのビルドし、ビルドできたらWebブラウザで開く
      # または
      $ cargo doc          # ドキュメントのビルドのみ行う
      ```

1. プログラムの作成
   - [`src/main.rs`](./src/main.rs)に解答となるプログラムを書きます。

1. テストケースの作成
   - TechFUL上でテストすることもできますが、手元でテストする事もできます。
   - [`tests/sample_inputs.rs`](./tests/sample_inputs.rs)ファイルには、ひな型となるテストケースが用意されています。
   - TechFULの問題文に書かれているサンプル入出力をこのファイルに書き写します。
     これにより`cargo test`でプログラムの動作が確認できるようになります（後述）。

1. テストケースの実行
   - 以下のコマンドでテストケースを実行し、テストにパスすることを確認します。

      ```console
      $ cargo test -j 1
      ```

      **実行例**

      ```console
      $ cargo test -j 1
          ...
          Finished dev [unoptimized + debuginfo] target(s) in 25.31s
           Running target/debug/deps/main-aae3efe8c7e14c29

      running 0 tests

      test result: ok. 0 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out

           Running target/debug/deps/sample_inputs-946c74199de6e6a4

      running 3 tests
      No
      test sample2 ... ok
      Yes
      test sample1 ... ok
      No
      test sample3 ... ok

      test result: ok. 3 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
      ```

   - `-j`オプションはテストケース実行の並列数を指定し、デフォルト値はCPUの論理コア数です。
     `-j 1`を指定すると、テストケースが複数あるときに、それらを1つずつ順番に実行するようになります。
   - 上の例では`No`や`Yes`のようにプログラムからの標準出力を表示しています。
     もしテストケースが並列に実行されると複数のテストケースからの標準出力が混ざって分かりにくくなります。
     `-j 1`の指定は、このようなときに便利です。


1. プログラムの提出
   - プログラムが完成した時は、`cargo make submit`でcargo-equipの結果がクリップボードにコピーします。
   - クリップボードの内容をTechFULの提出欄にペーストして提出します。
     `AC`を目指して頑張ってください。


## 使用可能なクレート

下記の条件に対応しているクレートのみ使用できます．

* cargo-equipで1ファイルにできる
* rust 1.39.0に対応している
* 2015 editionに対応している


## ライセンス / License

本リポジトリの内容は **MITライセンス** のもとで公開されています。
詳しくは[LICENSE][license-file]ファイルを参照してください。

[license-file]: ./LICENSE
