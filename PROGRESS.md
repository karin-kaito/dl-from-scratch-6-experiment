# 学習進捗チェックシート — ゼロから作るDeep Learning ❻

**使い方**: 1ファイルにつき「読了（本の該当節を読んだ）／実行（動かした）／改造（1箇所変えて挙動を確認した）」の3段階でチェック。
実行環境の目安: 🖥 = ローカル（CPUで可）、☁ = Colab（GPU必要）、△ = 内容次第（まずローカルで試し、遅すぎ/GPU必須ならColab）。

チェックの付け方: `[ ]` → `[x]`。メモ欄は自由記入。セッションの終わりに下部の「学習ログ」へ1行追記する。

---

## ch01 トークナイザ 🖥

| ファイル | 読了 | 実行 | 改造 | メモ |
|---|---|---|---|---|
| 01_char_tokenizer.py | [ ] | [x] | [ ] | 2026-07-13 Colabで実行済 / 2026-08-29 ローカル動作確認済 |
| 02_byte_tokenizer.py | [ ] | [x] | [ ] | Colab実行済(7〜8月) |
| 03_bpe_train.py | [ ] | [x] | [ ] | Colab実行済(7〜8月) |
| 04_bpe_tokenizer.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 05_special_token.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 06_pretokenize.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 07_tiny_codes.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 08_eval.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 09_bpe_encode.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |

## ch02 Attention・GPT-2 🖥

| ファイル | 読了 | 実行 | 改造 | メモ |
|---|---|---|---|---|
| 01_soft_dict.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 02_attn_math.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 03_attn_scaling.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 06_attn_mask.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 07_attn_value.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 08_multi_head.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 09_norm_gelu.py | [ ] | [ ] | [ ] | Colab実行済(7〜8月) |
| 10_gpt2.py | [ ] | [ ] | [ ] | 推論のみ。CPUでも可のはず / Colab実行済(7〜8月) |

## ch03 事前学習・SFT・GRPO（CodeBot）☁

| ファイル | 読了 | 実行 | 改造 | メモ |
|---|---|---|---|---|
| 01_pretrain.py | [ ] | [ ] | [ ] | ☁ runner.ipynb で実行 |
| 02_generate.py | [ ] | [ ] | [ ] | △ 学習済モデルがあればローカル可 |
| 03_alpaca.py | [ ] | [ ] | [ ] | 🖥 データ確認系なら |
| 03_sft.py | [ ] | [ ] | [ ] | ☁ |
| 04_chat.py | [ ] | [ ] | [ ] | △ |
| 09_grpo.py | [ ] | [ ] | [ ] | ☁ |

## ch04 BPEの高速化 🖥

| ファイル | 読了 | 実行 | 改造 | メモ |
|---|---|---|---|---|
| 01_bpe_optimize.py | [ ] | [ ] | [ ] | |
| 02_bpe_cache.py | [ ] | [ ] | [ ] | |
| 03_bpe_chunk.py | [ ] | [ ] | [ ] | |
| 04_bpe_parallel.py | [ ] | [ ] | [ ] | |
| 06_encode_optimize.py | [ ] | [ ] | [ ] | |
| 07_encode_parallel.py | [ ] | [ ] | [ ] | |

## ch05 モデル改良（RoPE/SwiGLU/RMSNorm/KVキャッシュ）🖥

| ファイル | 読了 | 実行 | 改造 | メモ |
|---|---|---|---|---|
| 01_rope.py | [ ] | [ ] | [ ] | |
| 02_swiglu.py | [ ] | [ ] | [ ] | |
| 03_rmsnorm.py | [ ] | [ ] | [ ] | |
| 04_improved_gpt.py | [ ] | [ ] | [ ] | |
| 05_kvcache.py | [ ] | [ ] | [ ] | |

## ch06 学習の改良（AdamW/スケジューラ/混合精度/DPO）△

| ファイル | 読了 | 実行 | 改造 | メモ |
|---|---|---|---|---|
| 02_adamw.py | [ ] | [ ] | [ ] | 🖥 |
| 03_lr_scheduler.py | [ ] | [ ] | [ ] | 🖥 |
| 04_mixed_precision.py | [ ] | [ ] | [ ] | ☁ GPU前提の内容 |
| 05_pretrain.py | [ ] | [ ] | [ ] | ☁ |
| 06_generate.py | [ ] | [ ] | [ ] | △ |
| 07_llm_judge.py | [ ] | [ ] | [ ] | △ |
| 08_dpo.py | [ ] | [ ] | [ ] | ☁ |
| 09_llm_judge.py | [ ] | [ ] | [ ] | △ |

## ch07 WebBot用トークナイザ 🖥

| ファイル | 読了 | 実行 | 改造 | メモ |
|---|---|---|---|---|
| 01_bpe_train.py | [ ] | [ ] | [ ] | データ量によっては△ |
| 02_bpe_encode.py | [ ] | [ ] | [ ] | |

## ch08（コードなし・読むのみ）

- [ ] 読了

## ch09 WebBot事前学習 ☁

| ファイル | 読了 | 実行 | 改造 | メモ |
|---|---|---|---|---|
| 01_pretrain.py | [ ] | [ ] | [ ] | ☁ 大規模。A100推奨 |
| 02_generate.py | [ ] | [ ] | [ ] | △ |

---

## 再開手順（/clear後・モデル変更後・VSCode起動でも同じ）

1. VSCode（またはアプリ）で `E:\work\deep-learning-from-scratch-6` を開き、Claude Code を起動
2. 「**続きから**」と入力するだけ（CLAUDE.md が自動で読み込まれ、Claude がこのファイルを見て現在地と次の1本を提案する）
3. 実行コマンドの基本形:
   ```
   PYTHONUTF8=1 uv run python ch01/02_byte_tokenizer.py
   ```
4. Colabが必要な回: Googleドライブの `dl-from-scratch-6/runner.ipynb` を開き、セル2の CHAPTER/SCRIPT を書き換えて上から実行

### VSCodeでセル単位実行（Colabのようにブロックごとに動かしたい場合）

各chXX/*.pyの `# %%` マーカーがそのままセル区切りとして使える（VSCode Python拡張のInteractive Window機能）。セットアップ済み事項:

- `ipykernel` は `.venv` にインストール済み（`uv add --dev ipykernel`）
- `.vscode/settings.json` で `python.defaultInterpreterPath` を `.venv` に固定済み

新しいVSCodeウィンドウ／別PCで開いた直後は、**カーネル選択だけ手動で1回必要**（インタープリター選択が自動でもJupyterカーネルは連動しないことがある）:

1. 対象の `.py` を開き、`# %%` セルの上で `Ctrl+Enter`（Interactive-1パネルが開く）
2. パネル右上「カーネルの選択」→「Python環境...」→ `dlfs6 (3.12.13) .venv\Scripts\python.exe` を選択（星マーク付きのはず）
3. 以降はそのウィンドウでは選び直し不要。ウィンドウを閉じて開き直した場合のみ再度必要になることがある
4. カーネル選択後もセルが「保留中」のまま動かない場合は、パネル左上の「割り込み」→「再起動」で復旧する（2026-08-29に実際に発生・復旧確認済み）

## 学習ログ（セッションごとに1行追記）

- 2026-07-13: ch01/01_char_tokenizer.py を Colab で実行（outputs/ch01 にログあり）
- 2026-08-29: 環境整理・方針決定。ローカルで ch01/01 動作確認（PYTHONUTF8=1 必要と判明）
- 2026-08-29: VSCode Interactive Windowでのセル単位実行をセットアップ（ipykernel追加、.vscode/settings.json、カーネル選択手順を確立）
- 2026-10-24: 約2か月ぶりに再開。現在地確認とプロジェクト整理のみ（学習は進めず）。Colab の run/ に ch01全9本・ch02全8本の実行出力が残っている（2026-07-13〜08-07）が本表に未反映 → 次回、反映するか ch01/04 からやり直すかを決める
- 2026-11-08〜09: 現状確認とプロジェクト整理（`プロジェクト整理_20261108-1953.md` を作成・git管理外）。Colab実行分をメモ欄に反映、未コミット分をコミット・push、`.tmp_cells/` 削除、.gitignore 整備。学習は進めず。**次は ch01/04_bpe_tokenizer.py をローカルで「読む→実行→1箇所改造」**
