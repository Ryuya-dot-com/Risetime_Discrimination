# リスニングタスク4（立ち上がり時間弁別）単体版

単体で実施する立ち上がり時間弁別タスクです。参加者向け UI ではダミーコード「リスニングタスク4」を表示し、研究者向けには本 README に実タスク名や刺激設定を記載しています。

## フロー
- 練習: 刺激 1 と 100 を用いた 5 試行。正誤フィードバックあり。
- 練習完了後: スペースキーまたは「本番を開始」ボタンで本番を開始（練習ボタンは無効化）。
- 本番: 最大 75 試行またはリバーサル 7 回で終了。フィードバックなし、進捗表示なし。
- 閾値: リバーサル平均を計算し画面表示。自動で CSV をダウンロード。

## 必要ファイル構成
```
risetime_discrimination/
  ├ Stimuli/1.flac ... Stimuli/101.flac
  ├ index.html
  └ risetime_discrimination.js
```

## 使い方
1. ブラウザで `index.html` を開く。
2. 参加者 ID を入力し、「説明へ進む」→「練習を開始」。
3. 練習 5 回終了後、スペースキーまたは「本番を開始」ボタンで本番を開始。
4. 終了後、CSV が自動ダウンロードされる（ファイル名: `<ID>_risetime_discrimination.csv`）。

## CSV 出力列
- `subject_id`, `trial`, `stimulus_step`, `odd_position`, `correct_answer`, `response`, `correct`, `rt_ms`
- `num_reversals_after`, `step_before`, `step_after`, `step_size_used`, `mean_reversal_so_far`

## パラメータ
- 本番試行: 最大 75 / リバーサル 7 回で終了
- 練習試行: 5（刺激 1 vs 100）、完了後に手動開始（スペース/ボタン）
- ISI: 500 ms / シーケンス後待機: 500 ms / 反応後: 1000 ms
- ステップサイズ: [10, 5, 2, 1, 1, 1, 1, 1]（自動階段法）
