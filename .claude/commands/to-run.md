---
description: 指定した章のPythonファイルをセル分割し、Colab用runフォルダへ変換出力する（本体は無変更）
argument-hint: [chapter/filename.py]  例: ch02/10_gpt.py
allowed-tools: Bash, Read, Write
---

対象ファイル: $ARGUMENTS

このリポジトリ内の `$ARGUMENTS` について、以下の手順を順番に実行してください。

1. 対象ファイルの中身を読み、内容を変更せずに一時作業フォルダ
   （例: `./.tmp_cells/` 配下、なければ作成）へ同名でコピーしてください。
   - リポジトリ本体（$ARGUMENTS そのもの）は絶対に編集しないこと

2. コピーした一時ファイルに対してのみ、処理の意味のあるまとまり
   （import部分、関数/クラス定義、実行部分の各ステップなど）ごとに
   `# %%` マーカーコメントを挿入してください。
   - ロジック自体は一切変更しないこと
   - 実行部分は1ステップ=1セル程度の粒度で、迷ったら細かく分けてよい

3. コピーした一時ファイルの中に、スクリプトの場所からリポジトリルートへ
   移動するイディオム（`__file__` を使って
   `os.chdir(os.path.dirname(os.path.abspath(__file__)), ...)` のような
   処理をしている箇所）が含まれる場合のみ、Colab上で動作するように
   その部分だけ次の内容に置き換えてください（他のロジックには一切触れないこと）。

   ```python
   import os, sys

   REPO_URL = "https://github.com/karin-kaito/dl-from-scratch-6-experiment.git"
   REPO_DIR = "dl-from-scratch-6-experiment"

   if not os.path.exists(REPO_DIR):
       os.system(f"git clone {REPO_URL}")
   os.chdir(REPO_DIR)
   sys.path.append('.')
   ```

   - このイディオムが存在しない場合は何もしなくてよい
   - `__file__` はColabのノートブック実行環境では定義されないため、
     このイディオムを含んだままだと実行時に `NameError` になる

4. まず `python -c "import jupytext"` を実行し、エラーが出なければ
   インストール済みとみなしてこの手順をスキップしてください。
   エラーが出た場合のみ `pip install jupytext` を実行してください。

5. マーカー入りの一時ファイルを、以下のルールでノートブック形式に変換し、
   Google Driveのrunフォルダへ出力してください。
   - 出力ファイル名: `$ARGUMENTS` のパスの `/` を `_` に置換し、拡張子を `.ipynb` に変更
     （例: ch02/10_gpt.py → ch02_10_gpt.ipynb）
   - 出力先: `G:\マイドライブ\Colab Notebooks\dl-from-scratch-6\run\`
     （このマシンでのGoogleドライブのマウント先パスが異なる場合は実際のパスに置き換えて実行）

6. 変換が成功したら、出力先ファイルが実際に存在することを確認し、
   セルがいくつに分かれたか教えてください

7. 一時作業フォルダ内のファイルはそのまま残してよい（次回上書きされる）

注意: このコマンドは git commit / push を一切行いません。
本体コードに実質的な修正（バグ修正・コメント改善など）が発生した場合は、
別途その旨を伝えてください。その場合のみ、通常の編集・commit手順に進みます。
