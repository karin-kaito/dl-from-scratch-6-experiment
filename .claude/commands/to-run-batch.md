---
description: 指定した章のPythonファイル（複数指定 or フォルダ一括）をセル分割し、Colab用runフォルダへ変換出力する（本体は無変更）
argument-hint: [file1.py file2.py ...] または [chapter_folder]  例: ch01/01_char_tokenizer.py ch01/02_byte_tokenizer.py  /  ch01
allowed-tools: Bash, Read, Write
---

指定: $ARGUMENTS

まず対象ファイルの一覧を以下のルールで確定してください。

- `$ARGUMENTS` がスペース区切りで複数のファイルパス（例: `ch01/01_x.py ch01/02_y.py`）の場合、
  それぞれを対象ファイルとする
- `$ARGUMENTS` がフォルダ名のみ（例: `ch01`）の場合、そのフォルダ直下の
  `*.py` ファイルすべてを対象ファイルとする（サブフォルダは含めない）
- 対象ファイルが1件も見つからない場合は、その旨を報告して処理を中断する

対象ファイル一覧が確定したら、**各ファイルについて以下の1〜6を順番に繰り返してください**
（1ファイルごとに完了させてから次のファイルに進む。並列実行はしない）。

1. 対象ファイルの中身を読み、内容を変更せずに一時作業フォルダ
   （例: `./.tmp_cells/` 配下、なければ作成）へ同名でコピーしてください。
   - リポジトリ本体（対象ファイルそのもの）は絶対に編集しないこと

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

4. `python -c "import jupytext"` を実行し、エラーが出なければインストール済みとみなして
   スキップする。エラーが出た場合のみ `pip install jupytext` を実行する
   （このチェックは全ファイル処理の最初に1回だけ行えばよい）

5. マーカー入りの一時ファイルを、以下のルールでノートブック形式に変換し、
   Google Driveのrunフォルダへ出力してください。
   - 出力ファイル名: 元のパスの `/` を `_` に置換し、拡張子を `.ipynb` に変更
     （例: ch01/02_byte_tokenizer.py → ch01_02_byte_tokenizer.ipynb）
   - 出力先: `G:\マイドライブ\Colab Notebooks\dl-from-scratch-6\run\`
     （このマシンでのGoogleドライブのマウント先パスが異なる場合は実際のパスに置き換えて実行）

6. 変換が成功したら、出力先ファイルが実際に存在することを確認する

全ファイルの処理が終わったら、最後に一覧形式でまとめて報告してください
（ファイル名／セル分割数／成功可否）。

注意: このコマンドは git commit / push を一切行いません。
本体コードに実質的な修正（バグ修正・コメント改善など）が発生した場合は、
別途その旨を伝えてください。その場合のみ、通常の編集・commit手順に進みます。
