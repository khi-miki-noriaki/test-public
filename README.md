# Git 操作に関するメモ

以下の環境で実施

* Windows 10 Pro 21H2
* git for windows version 2.35.2.windows.1

## 2要素認証ありでの https clone 手順

## SSH 接続の Clone 手順(失敗)

ssh で行いたいのだが、Proxy 環境下ではうまくいかなかった...

やったことをメモとして残しておく

参考サイト: [大学のプロキシに通してgithub(とssh)を使う](https://qwerty.hateblo.jp/entry/2018/07/07/171205)

* 以下の設定を `~/.ssh/config` に設定

  ```conf
  Host github.com.khi
      HostName github.com
      ProxyCommand "C:\Program Files\Git\mingw64\bin\connect.exe" -H <proxy user>@<proxy url>:<port> %h %p
      User git
      Port 22
      IdentityFile ~/.ssh/github-khi
      TCPKeepAlive yes
      IdentitiesOnly yes
  ```

* 以下のコマンドをコマンドプロンプトで入力

  ```sh
  > ssh -T git@github.com.khi
  ```
  
* 何のメッセージも表示されずに終了...
