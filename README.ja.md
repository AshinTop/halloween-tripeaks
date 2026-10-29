[English](README.md) | [简体中文](README.zh-CN.md) | [Español](README.es.md) | [Português (Brasil)](README.pt-BR.md) | [日本語](README.ja.md)

# 🎃 Trick-or-Treat TriPeaks — 月の橋で遊ぶハロウィン・ソリティア

**3 つの塔、お菓子の道、そして月明かりの近道。** Trick-or-Treat TriPeaks は [FreeCell Game](https://freecell-game.top/) のために作られたハロウィンのソリティアです。隣り合う数字のカードをつなぎ、山を片づけ、連続で取ったごほうびの「月の橋」で難しい場面を越えましょう。黒猫の J、魔女の Q、かぼちゃの K はオリジナルの絵柄です。

**[今すぐ遊ぶ](https://halloween-tripeaks.crazy3d.org/)** · [ハロウィンゲーム集](https://github.com/AshinTop/halloween-games) · [埋め込みガイド](EMBEDDING.md) · [設計ノート](DESIGN.md)

**README の言語：** English、简体中文、Español、Português (Brasil)、日本語。**ゲーム内の表示は英語と簡体字中国語のみ**です。日本語などの README があっても、ゲームのメニューがその言語に対応しているわけではありません。

![3 つの山、山札、捨て札、月の橋メーターが並ぶハロウィン TriPeaks](docs/images/gameplay.jpg)

## カードの中身 👻

- **全 52 枚**。場の 3 つの山に 28 枚、山札に 23 枚、最初の捨て札に 1 枚を使います。
- **Journey は 8 問**。いずれも山札を引かずに勝てる手順を検証しています。
- 同じ配置を再現できる Classic と、UTC の日付で決まる Daily。
- 回数制限のある月の橋、取り消し、合法手のヒント、星、ローカル保存、任意の合成音に対応します。

## 山を片づけるには

捨て札より数字が 1 つ大きいか小さい、表に出たカードを取ります。取ったカードが次の捨て札になります。色やマークは関係なく、A と K はつながるため **K–A–2** も有効です。上に重なるカードが 1 枚でも残っていれば、そのカードは取れません。場の 28 枚をすべて取るとクリアです。

山札は好きなときに引けますが、連続取りはリセットされます。23 枚を使い切った後の配り直しはありません。「山札が空」「取れる表のカードがない」「月の橋もない」の 3 条件がそろうと失敗になります。

通常の取り方で 5 枚連続して取ると、**月の橋**を獲得できます。持てるのは同時に 1 つ、獲得は 1 ゲームで最大 2 つです。橋を選んでから表のカードを選ぶと、数字に関係なく取れます。重なっているカードには使えません。使うと連続取りが切れ、もう一度ボタンを押すと選択を解除できます。取り消しではカード、山札、得点、魔法が戻ります。

通常は 10 点に現在の連続数 × 5 を加算し、山の頂点のカードには 50 点を加算します。橋では基本の 10 点と、該当する頂点ボーナスを得ます。山札を引かずにクリアすると星 3 つ、5 回以内なら 2 つ、それ以外のクリアは 1 つ。時間制限はありません。

## 操作

| 操作 | 方法 |
|---|---|
| カードを取る | クリック・タップ、または Tab と Enter |
| 山札を引く | 山札を押す。ボタンや入力欄の外では Space |
| 魔法 | 月の橋を選んでから表のカード |
| 取り消し | Z またはボタン |
| 合法な一手を表示 | Spot a Move |
| 同じ配置で再挑戦・モード変更 | Restart と選択欄 |

**Spot a Move は今できる一手の案内です。** 最後まで解く機能ではなく、そのカードを取れば必ず勝てるという意味でもありません。

## 配置を選ぶ・共有する

[Journey 1](https://halloween-tripeaks.crazy3d.org/?level=1) が固定問題の入口です。[Classic のシード 12345](https://halloween-tripeaks.crazy3d.org/?mode=classic&seed=12345) では同じシャッフルを共有できます。Classic を選び直すと新しい配置、Restart なら同じ配置です。[日付指定の Daily](https://halloween-tripeaks.crazy3d.org/?mode=daily&date=2026-10-31) はその UTC 日付を保ちます。

進行中のゲーム、記録、設定はローカルに保存します。URL で指定した配置がある場合は、そちらを開始します。取り消し履歴はページを開いている間だけです。

## よくある質問

**すべての配置に解答がありますか？** Journey の 8 問は検証済みです。ランダムな Classic と Daily は、必ず解けるとは限りません。

**橋で下に隠れたカードを取れますか？** 取れません。数字の条件だけを変える魔法です。

**山札を再利用できますか？** できません。引くタイミング、長い連続取り、橋の使いどころを考えるゲームです。

## スクリーンショットと動画

![カードの隅の数字、捨て札、月の橋を見やすく配置した小さな TriPeaks 画面](docs/images/mobile.jpg)

実際のブラウザーで、小さな iframe 内の画面を撮影しています。画面構成を示す画像であり、実機スマートフォンの性能テストではありません。

[24 秒の紹介動画を見る](https://halloween-tripeaks.crazy3d.org/intro.html) · [字幕付き MP4 をダウンロード](docs/media/intro.mp4)。無音の動画は実際のゲーム画面を並べた紹介で、連続したプレイの録画ではありません。画像や動画は撮影時点の画面を記録しており、その後の演出変更が含まれない場合があります。

## 自分のサイトに埋め込む

```html
<iframe src="https://halloween-tripeaks.crazy3d.org/"
  title="Trick-or-Treat TriPeaks"
  style="display:block;width:100%;height:654px;border:0"
  allow="fullscreen" allowfullscreen></iframe>
```

カードはデスクトップ、細い縦長、背の低い横長のプレイヤー領域に合わせて調整されます。iframe の高さを実際に確保し、カードの隅の数字が読める余裕を残してください。親文書へのアクセス、カメラ、マイク、ポインターロックは不要です。

公開版は、この GitHub リポジトリと連携して Cloudflare にデプロイされています。iframe に高さを指定し、親サイトのツールバー用の領域も確保してください。全画面ボタンは親サイト側で用意できます。詳細は [EMBEDDING.md](EMBEDDING.md) を参照してください。

## ローカルで実行・確認する

```sh
python3 -m http.server 4173
```

リポジトリのルートでサーバーを起動し、[http://localhost:4173/](http://localhost:4173/) を開きます。静的なゲームなので、ビルドや依存パッケージのインストールは不要です。`file://` では ES モジュールが読み込めない場合があるため、HTTP(S) を使用してください。テストには Node.js が必要です。

```sh
npm test
```

**12 件のテスト**で Journey 全 8 問の解答、カードの重複、重なり、A/K 接続、山札、橋の獲得と上限、失敗条件、シャッフルの再現、日付リンク、保存データを確認します。

ゲームのソースはアカウント、外部 API、広告 SDK、外部素材 CDN を必要としません。記録はブラウザー内に保存され、クラウド同期はありません。Cloudflare が独自のホスティング用スクリプトやリクエストログを追加する場合があります。任意の合成音声はブラウザーの再生許可に従います。

## 月明かりの下でもうひと遊び 🍬

- [Haunted FreeCell](https://halloween-freecell.crazy3d.org/) · [ソース](https://github.com/AshinTop/halloween-freecell) — 定番 FreeCell と Lantern Rescue の終盤パズル.
- [Pumpkin Shift](https://halloween-pumpkin-shift.crazy3d.org/) · [ソース](https://github.com/AshinTop/halloween-pumpkin-shift) — Moon Glide を使う数字スライドパズル.
- [Witch’s Candy Blocks](https://halloween-block-blast.crazy3d.org/) · [ソース](https://github.com/AshinTop/halloween-block-blast) — 8×8 の盤面にキャンディーブロックを配置.
- [Pumpkin 2048](https://halloween-2048.crazy3d.org/) · [ソース](https://github.com/AshinTop/halloween-2048) — 定番の数字合成と Lantern Trials.

## 制作クレジットと応援

**AshinTop の Midnight Candy Club** のために、人が方向づける AI との協働で企画、プログラミング、文章、テスト、レビューを行いました。オリジナルの絵と合成音は、このプロジェクト向けに制作しています。[設計ノート](DESIGN.md) もご覧ください。

楽しめたら、**[GitHub で Trick-or-Treat TriPeaks に Star を付けてください](https://github.com/AshinTop/halloween-tripeaks)**。あとで見つけやすくなり、更新を追う目印にもなります。不具合の報告には、ステージやモード、ブラウザー、画面サイズ、再現手順を添えると助かります。[ハロウィンゲームの全コレクション](https://github.com/AshinTop/halloween-games) もどうぞ。
