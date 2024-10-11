# 自分が頻繁に使う言語のコンテナの作成
自分が頻繁に使うので作成しました。

## Cloneするとき
一部分だけCloneすればいいので、以下のコマンドを使えばＯＫです
> 以下のコマンドはhttps://zenn.dev/shti_f/articles/4d61be4da742ea を参考にしました
```bash
$ git clone --filter=blob:none --sparse ${REMOTE_URL}
$ git sparse-checkout set ${DIRECTORY_NAME}
```
