# Tm Calculator

A single-file, browser-based tool for choosing a primer region within a longer sequence.
Paste the sequence once, then move the two ends of the selection one base at a time while watching length, GC content and Tm.
No installation, no server: your sequence never leaves your browser. The user interface is currently in Japanese only.

長めの配列を一度読み込んだあと、プライマーにする範囲の両端を動かしながら、長さ・GC 含量・Tm を確かめるツールです。
`index.html` 1ファイルで動きます。インストールもサーバーも不要です。

## 使う

- オンライン: https://mkameya.github.io/tm-calculator/
- オフライン: `index.html` をダウンロードして Chrome / Edge で開く。

読み込んだ配列はブラウザの中だけで処理され、外部には送信されません。

## ねらい

プライマーを設計するとき、配列を端から削りながら Tm を見ていくと、削りすぎたときに全長を貼り直すことになります。
このツールは配列全体を保ったまま「選択範囲の両端」だけを動かすので、伸ばすのも削るのも同じ操作で行えます。

## できること

- **読み込み**: 貼り付け、クリップボード、テキスト／FASTA ファイルのドラッグ＆ドロップ。数字・空白・改行は自動で取り除きます。複数の配列を含む FASTA は、配列ごとに区切って表示します。
- **範囲の選択**: 配列の上をドラッグして大まかに選び、ボタンかキーで両端を1塩基ずつ調整。範囲ごと移動（長さ固定）もできます。位置を数値で指定することもできます。
- **相補鎖**: 表示する鎖の切り替え。選択範囲とその相補鎖（5′→3′ 向き。リバースプライマーとしてそのまま使える向き）をそれぞれコピーできます。
- **計算**: 長さ、GC 含量、Tm（最近接塩基対法・GC 法・Wallace 法）。縮重塩基を含む範囲では、取りうる値の最小–最大を表示します。
- **その他**: 元に戻す。配列と選択範囲はブラウザに保存され、次に開いたとき復元されます。

## 基本の流れ

1. 配列を貼り付ける（またはファイルをドロップする）。
2. プライマーにしたいあたりをドラッグして選ぶ。
3. `←` `→`（範囲ごと移動）、`Shift`+`←` `→`（3′端）、`Ctrl`+`←` `→`（5′端）で調整する。
4. 「コピー」で配列を取り出す。

操作の詳細は画面右上の「？ 使い方」に書いてあります。

## Tm の計算方法

| 方法 | 内容 |
|---|---|
| 最近接塩基対法 | SantaLucia (1998) の統一パラメータと同論文の塩補正。Na⁺ 50 mM、プライマー 0.5 µM。Mg²⁺ は考慮していません |
| GC 法 | Tm = 59.9 + 0.41 × GC含量(%) − 500 ÷ 長さ |
| Wallace 法 | Tm = 2 × (A と T の数) + 4 × (G と C の数) |

参考文献: SantaLucia J Jr. (1998) A unified view of polymer, dumbbell, and oligonucleotide DNA nearest-neighbor thermodynamics. Proc Natl Acad Sci USA 95:1460–1465.

## 注意

- Chrome / Edge を想定しています。画面は日本語のみです。
- 塩濃度とプライマー濃度は固定で、画面からは変えられません。
- GenBank 形式には対応していません（配列部分だけを貼ってください）。
- 想定している長さは数万塩基までです。

## ライセンス

MIT License（`LICENSE` を参照）。
