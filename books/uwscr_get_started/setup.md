---
title: "セットアップと実行方法"
free: true
---

# UWSCRのダウンロード

[最新リリース](https://github.com/stuncloud/UWSCR/releases/latest) のページ下部にある`Assets`からzipファイル[^1]をダウンロードし、任意のフォルダに`uwscr.exe`を展開してください。

# 実行方法

## スクリプトの実行

```powershell
uwscr hoge.uws
```

`hoge.uws` は任意のスクリプトファイルです

## Repl

対話モードでスクリプトを実行できます。
現時点では入力補完等の便利な機能は実装されていません。

Explorer等から`uwscr.exe`をダブルクリックした場合はCUIが表示されReplモードで起動します

PowerShell等から実行する場合は`cmd`経由で実行してください

```powershell
cmd /c uwscr # コマンドラインオプションを渡さなければReplモードで起動
# cmd /c uwscr --repl # 明示的にreplを実行
```

## その他の実行方法

以下で確認できます。

```powershell
cmd /c uwscr --help
```

または[UWSCR Wiki](https://github.com/stuncloud/UWSCR/wiki#%E5%AE%9F%E8%A1%8C%E6%96%B9%E6%B3%95)を参照ください。

[^1]: 環境に合わせてx64かx86を選んでください