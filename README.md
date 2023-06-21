# Momento CLI

Momento のCLIを体感する。

## セットアップ

ここ参照
https://github.com/momentohq/momento-cli/blob/main/README.md

### MacOSの場合

```sh
brew tap momentohq/tap
brew install momento-cli
```

すでにインストールしている場合は以下のコマンドでアップグレードします。

```sh
brew upgrade momento-cli
```

アップグレード時に再インストールを聞かれた場合

```text
brew install momento-cli
Running `brew update --auto-update`...
==> Auto-updated Homebrew!
Updated 3 taps (hashicorp/tap, homebrew/core and homebrew/cask).
==> New Formulae
cargo-generate      getmail6            minigraph           typical
==> New Casks
command-x                  frappe-books               graalvm-jdk

You have 1 outdated formula installed.

Warning: momentohq/tap/momento-cli 0.40.0 is already installed and up-to-date.
To reinstall 0.40.0, run:
  brew reinstall momento-cli
```

以下のコマンドを実行します。

```sh
brew reinstall momento-cli
```

```text
==> Fetching momentohq/tap/momento-cli
==> Downloading https://github.com/momentohq/momento-cli/releases/download/v0.40
Already downloaded: /Users/{accountid}/Library/Caches/Homebrew/downloads/72f36c97e8b8dc3bf2688d8e849967d86d871ba3cbde867b7dd4b5ae53ee0be8--momento-cli-0.40.0.aarch64-apple-darwin.tar.gz
==> Reinstalling momentohq/tap/momento-cli
==> Caveats
zsh completions have been installed to:
  /opt/homebrew/share/zsh/site-functions
==> Summary
🍺  /opt/homebrew/Cellar/momento-cli/0.40.0: 5 files, 9MB, built in 1 second
==> Running `brew cleanup momento-cli`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
```

最後にクリーンアップします。

```sh
brew cleanup momento-cli
```

## getting started

とりあえず、`momento`と入力してみましょう。

```sh
momento
```

　実行結果

```text
Command line tool for Momento Serverless Cache

Usage: momento [OPTIONS] <COMMAND>

Commands:
  cache      Interact with caches
  topic      Interact with topics
  configure  Configure credentials
  help       Print this message or the help of the given subcommand(s)

Options:
      --verbose            Log more information
  -p, --profile <PROFILE>  User profile [default: default]
  -h, --help               Print help
  -V, --version            Print version
```

### バージョンを調べる

```sh
momento --version
```

今回はバージョン0.40 を利用します。

```
momento 0.40.0
```

### config を設定する

```sh
momento configure --quick
```

セットアップには事前にトークンを取得する必要があります。
トークンの取得方法は[こちら](https://docs.momentohq.com/ja/getting-started)です。

トークンがどこに保存されるかを調べるには以下のコマンドを実行します。

```sh
cat ~/.momento/credentials
```

### helpを開く

使い方がわからなくなったら以下のコマンドを実行します。

```sh
momento --help
```

　実行結果

```text
Command line tool for Momento Serverless Cache

Usage: momento [OPTIONS] <COMMAND>

Commands:
  cache      Interact with caches
  topic      Interact with topics
  configure  Configure credentials
  help       Print this message or the help of the given subcommand(s)

Options:
      --verbose            Log more information
  -p, --profile <PROFILE>  User profile [default: default]
  -h, --help               Print help
  -V, --version            Print version
```

## 廃止されたコマンド

以下のコマンドはv0.40では廃止されているようです。

```sh
momento account signup
```

## トラブルシューティング

```
ERROR: Unauthenticated { description: "unauthenticated", source: TonicStatus(Status { code: Unauthenticated, message: "Could not validate authorization header", metadata: MetadataMap { headers: {"content-type": "application/grpc", "server": "envoy", "momento_ver": "3.62.1", "content-length": "0", "access-control-allow-origin": "*", "vary": "origin,access-control-request-method,access-control-request-headers", "access-control-expose-headers": "grpc-status,grpc-message,grpc-encoding,grpc-accept-encoding", "date": "Wed, 21 Jun 2023 15:27:52 GMT", "x-envoy-upstream-service-time": "0"} }, source: None }) }
```
