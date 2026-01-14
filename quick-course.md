---
layout: default
title: クイックコース
description: 統計学の基礎を最短で学ぶ厳選問題集
permalink: /quick-course/
---

# クイックコース

<div class="quick-course-banner" style="background: linear-gradient(135deg, #159957 0%, #0d6942 100%);">
  <h2>最短で統計学の基礎をマスター</h2>
  <p>各分野から厳選した40問で、統計学の重要概念を効率よく学習できます。</p>
</div>

## このコースについて

- **対象**: 統計学を短期間で学びたい方、復習したい方
- **所要時間**: 約3-4時間（目安）
- **問題数**: 40問（各分野5問ずつ）
- **特徴**: 理論の理解に直結する問題を厳選

---

## 学習の進め方

1. 各セクションの理論ページを先に読む（リンク付き）
2. 厳選問題を解く
3. 解答を確認し、理解を深める
4. 苦手な分野は追加問題で練習

---

## 1. 記述統計の基礎

<p class="related-link">理論: <a href="{{ site.baseurl }}/theory/mean-median-mode/">平均・中央値・最頻値</a> / <a href="{{ site.baseurl }}/theory/variance-std/">分散と標準偏差</a></p>

### Q1-1: 平均の計算 <span class="difficulty-badge difficulty-1">基本</span>

あるクラスの生徒5人のテスト点数が 60, 70, 80, 90, 100 点でした。平均点を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

$$\bar{x} = \frac{60 + 70 + 80 + 90 + 100}{5} = \frac{400}{5} = 80$$

**答え: 80点**

</details>

### Q1-2: 中央値の理解 <span class="difficulty-badge difficulty-1">基本</span>

データ: 3, 7, 2, 9, 5 の中央値を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

データを昇順に並べる: 2, 3, **5**, 7, 9

5個のデータの真ん中（3番目）は **5**

**答え: 5**

</details>

### Q1-3: 標準偏差の計算 <span class="difficulty-badge difficulty-2">標準</span>

データ: 2, 4, 6, 8, 10 の標本標準偏差を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

1. 平均: $\bar{x} = 6$
2. 偏差の2乗: $(-4)^2 + (-2)^2 + 0^2 + 2^2 + 4^2 = 16+4+0+4+16 = 40$
3. 標本分散: $s^2 = \frac{40}{4} = 10$
4. 標準偏差: $s = \sqrt{10} \approx 3.16$

**答え: 約3.16**

</details>

### Q1-4: 平均と中央値の比較 <span class="difficulty-badge difficulty-2">標準</span>

以下のデータについて、平均と中央値を比較し、どちらが代表値として適切か考えてください。

データ: 10, 12, 11, 13, 100（万円の年収）

<details markdown="1">
<summary>解答を見る</summary>

- 平均: $(10+12+11+13+100)/5 = 29.2$ 万円
- 中央値: 11, 12, **12**, 13, 100 → 12万円（並び替え後）

100万円という外れ値があるため、**中央値（12万円）の方が適切**。平均は外れ値に引っ張られて実態より高くなっている。

</details>

### Q1-5: 68-95-99.7ルール <span class="difficulty-badge difficulty-2">標準</span>

ある製品の重量は平均500g、標準偏差10gの正規分布に従います。重量が480gから520gの間にある製品の割合は約何%ですか？

<details markdown="1">
<summary>解答を見る</summary>

480g = 500 - 20 = $\mu - 2\sigma$
520g = 500 + 20 = $\mu + 2\sigma$

68-95-99.7ルールより、平均±2標準偏差に約95%が含まれる。

**答え: 約95%**

</details>

---

## 2. 確率の基礎

<p class="related-link">理論: <a href="{{ site.baseurl }}/theory/probability-basics/">確率の基本概念</a> / <a href="{{ site.baseurl }}/theory/conditional-probability/">条件付き確率</a></p>

### Q2-1: 基本的な確率 <span class="difficulty-badge difficulty-1">基本</span>

サイコロを1回振るとき、4以上が出る確率を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

4以上: {4, 5, 6} の3通り
全体: 6通り

$$P(4以上) = \frac{3}{6} = \frac{1}{2}$$

**答え: 1/2（50%）**

</details>

### Q2-2: 余事象 <span class="difficulty-badge difficulty-1">基本</span>

コインを3回投げるとき、「少なくとも1回は表が出る」確率を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

余事象「3回とも裏」を使う:

$$P(3回とも裏) = \left(\frac{1}{2}\right)^3 = \frac{1}{8}$$

$$P(少なくとも1回表) = 1 - \frac{1}{8} = \frac{7}{8}$$

**答え: 7/8（87.5%）**

</details>

### Q2-3: 条件付き確率 <span class="difficulty-badge difficulty-2">標準</span>

100人の学生のうち、数学が得意な人は40人、物理が得意な人は30人、両方得意な人は20人です。数学が得意な人の中で、物理も得意な人の割合は？

<details markdown="1">
<summary>解答を見る</summary>

$$P(物理得意|数学得意) = \frac{P(両方得意)}{P(数学得意)} = \frac{20/100}{40/100} = \frac{20}{40} = 0.5$$

**答え: 50%**

</details>

### Q2-4: 独立事象 <span class="difficulty-badge difficulty-2">標準</span>

製品Aの不良率は2%、製品Bの不良率は3%です。両方とも不良品である確率は？（独立と仮定）

<details markdown="1">
<summary>解答を見る</summary>

独立なので:

$$P(A不良 \cap B不良) = P(A不良) \times P(B不良) = 0.02 \times 0.03 = 0.0006$$

**答え: 0.06%（0.0006）**

</details>

### Q2-5: 期待値 <span class="difficulty-badge difficulty-2">標準</span>

くじ引きで、1等（1万円）が10%、2等（1000円）が20%、はずれ（0円）が70%です。1回のくじ引きの期待値は？

<details markdown="1">
<summary>解答を見る</summary>

$$E[X] = 10000 \times 0.1 + 1000 \times 0.2 + 0 \times 0.7$$
$$= 1000 + 200 + 0 = 1200$$

**答え: 1200円**

</details>

---

## 3. 確率分布

<p class="related-link">理論: <a href="{{ site.baseurl }}/theory/normal-distribution/">正規分布</a> / <a href="{{ site.baseurl }}/theory/binomial/">二項分布</a></p>

### Q3-1: z値の計算 <span class="difficulty-badge difficulty-1">基本</span>

平均70点、標準偏差10点の試験で、85点のz値を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

$$z = \frac{x - \mu}{\sigma} = \frac{85 - 70}{10} = 1.5$$

**答え: z = 1.5**

</details>

### Q3-2: 正規分布の確率 <span class="difficulty-badge difficulty-2">標準</span>

身長が平均170cm、標準偏差5cmの正規分布に従うとき、175cm以上の人の割合は？（$P(Z<1)=0.8413$）

<details markdown="1">
<summary>解答を見る</summary>

$$z = \frac{175 - 170}{5} = 1.0$$

$$P(X > 175) = P(Z > 1) = 1 - P(Z < 1) = 1 - 0.8413 = 0.1587$$

**答え: 約15.9%**

</details>

### Q3-3: 二項分布 <span class="difficulty-badge difficulty-2">標準</span>

打率3割の打者が5打席に立つとき、ちょうど2本ヒットを打つ確率は？

<details markdown="1">
<summary>解答を見る</summary>

$n=5$, $k=2$, $p=0.3$

$$P(X=2) = \binom{5}{2}(0.3)^2(0.7)^3 = 10 \times 0.09 \times 0.343 = 0.3087$$

**答え: 約30.9%**

</details>

### Q3-4: パーセンタイル <span class="difficulty-badge difficulty-2">標準</span>

IQは平均100、標準偏差15の正規分布に従います。上位2.5%に入るIQは何以上？（$z=1.96$で上位2.5%）

<details markdown="1">
<summary>解答を見る</summary>

$$x = \mu + z \times \sigma = 100 + 1.96 \times 15 = 100 + 29.4 = 129.4$$

**答え: 約130以上**

</details>

### Q3-5: 中心極限定理 <span class="difficulty-badge difficulty-3">発展</span>

母集団の平均が50、標準偏差が12のとき、n=36の標本平均の標準誤差は？

<details markdown="1">
<summary>解答を見る</summary>

$$SE = \frac{\sigma}{\sqrt{n}} = \frac{12}{\sqrt{36}} = \frac{12}{6} = 2$$

**答え: 2**

</details>

---

## 4. 推定と検定

<p class="related-link">理論: <a href="{{ site.baseurl }}/theory/interval-estimation/">区間推定</a> / <a href="{{ site.baseurl }}/theory/hypothesis-testing/">仮説検定の基礎</a></p>

### Q4-1: 信頼区間 <span class="difficulty-badge difficulty-2">標準</span>

標本平均50、標準誤差2のとき、95%信頼区間を求めてください。（$z=1.96$）

<details markdown="1">
<summary>解答を見る</summary>

$$50 \pm 1.96 \times 2 = 50 \pm 3.92$$

**答え: 46.08 から 53.92**

</details>

### Q4-2: 仮説の設定 <span class="difficulty-badge difficulty-1">基本</span>

「新薬は従来薬より効果がある」を検証したい場合、帰無仮説と対立仮説を設定してください。

<details markdown="1">
<summary>解答を見る</summary>

- 帰無仮説 $H_0$: 新薬と従来薬に差がない（$\mu_{新} = \mu_{従来}$）
- 対立仮説 $H_1$: 新薬の方が効果がある（$\mu_{新} > \mu_{従来}$）

**片側検定（右側）**になります。

</details>

### Q4-3: p値の解釈 <span class="difficulty-badge difficulty-2">標準</span>

検定の結果、p値が0.03でした。有意水準5%で帰無仮説を棄却できますか？

<details markdown="1">
<summary>解答を見る</summary>

$p = 0.03 < \alpha = 0.05$ なので、**帰無仮説を棄却できる**。

統計的に有意な差があると言える。

</details>

### Q4-4: 検定統計量 <span class="difficulty-badge difficulty-2">標準</span>

母平均100を検定。標本平均104、標準偏差15、n=25のときのz値は？

<details markdown="1">
<summary>解答を見る</summary>

$$z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}} = \frac{104 - 100}{15/\sqrt{25}} = \frac{4}{3} \approx 1.33$$

**答え: z = 1.33**

</details>

### Q4-5: 第1種・第2種の誤り <span class="difficulty-badge difficulty-2">標準</span>

「効果がない薬を効果ありと判断する」のは第何種の誤りですか？

<details markdown="1">
<summary>解答を見る</summary>

帰無仮説（効果がない）が正しいのに、それを棄却してしまう誤り。

**答え: 第1種の誤り（Type I Error）**

</details>

---

## 5. 相関と回帰

<p class="related-link">理論: <a href="{{ site.baseurl }}/theory/correlation/">相関分析</a> / <a href="{{ site.baseurl }}/theory/regression/">単回帰分析</a></p>

### Q5-1: 相関係数の解釈 <span class="difficulty-badge difficulty-1">基本</span>

相関係数 r = -0.8 はどのような関係を示しますか？

<details markdown="1">
<summary>解答を見る</summary>

- 符号がマイナス → **負の相関**（一方が増えると他方が減る）
- 絶対値0.8 → **強い相関**

**答え: 強い負の相関**

</details>

### Q5-2: 決定係数 <span class="difficulty-badge difficulty-2">標準</span>

相関係数 r = 0.7 のとき、決定係数 $R^2$ は？

<details markdown="1">
<summary>解答を見る</summary>

$$R^2 = r^2 = 0.7^2 = 0.49$$

**答え: 0.49（49%がxで説明される）**

</details>

### Q5-3: 回帰直線 <span class="difficulty-badge difficulty-2">標準</span>

回帰式 $\hat{y} = 10 + 2x$ で、x=5のときのyの予測値は？

<details markdown="1">
<summary>解答を見る</summary>

$$\hat{y} = 10 + 2 \times 5 = 10 + 10 = 20$$

**答え: 20**

</details>

### Q5-4: 回帰係数の解釈 <span class="difficulty-badge difficulty-2">標準</span>

広告費(万円)と売上(万円)の回帰式が $\hat{y} = 100 + 5x$ のとき、傾き5の意味は？

<details markdown="1">
<summary>解答を見る</summary>

広告費を**1万円増やすと、売上が約5万円増加する**ことを意味する。

</details>

### Q5-5: 相関と因果 <span class="difficulty-badge difficulty-3">発展</span>

「アイスクリームの売上と溺死者数に正の相関がある」から、「アイスが溺死を引き起こす」と言えますか？

<details markdown="1">
<summary>解答を見る</summary>

**言えない**。これは「見せかけの相関」（疑似相関）。

両方とも「気温（暑さ）」という**第三の変数（交絡因子）**の影響を受けている。暑いとアイスが売れ、暑いとプールに行く人が増えて溺死も増える。

**相関関係 ≠ 因果関係**

</details>

---

## 6. 実践問題

<p class="related-link">理論: <a href="{{ site.baseurl }}/problems/real-data-analysis/">実データを使った分析問題</a></p>

### Q6-1: データの読み取り <span class="difficulty-badge difficulty-2">標準</span>

A店の売上: 平均100万円、標準偏差20万円
B店の売上: 平均100万円、標準偏差5万円

どちらの売上が安定していますか？

<details markdown="1">
<summary>解答を見る</summary>

標準偏差が小さいほどばらつきが少なく安定している。

**答え: B店（標準偏差5万円）の方が安定**

</details>

### Q6-2: 外れ値の影響 <span class="difficulty-badge difficulty-2">標準</span>

データ: 10, 12, 11, 13, 14, 200

外れ値（200）を除く前と後で、平均はどう変わりますか？

<details markdown="1">
<summary>解答を見る</summary>

- 除く前: $(10+12+11+13+14+200)/6 = 43.3$
- 除いた後: $(10+12+11+13+14)/5 = 12$

**答え: 43.3 → 12（外れ値により平均が大きく歪んでいた）**

</details>

### Q6-3: A/Bテスト <span class="difficulty-badge difficulty-3">発展</span>

デザインA: 1000人中45人がクリック（4.5%）
デザインB: 1000人中55人がクリック（5.5%）

この差は実務的に意味がありますか？

<details markdown="1">
<summary>解答を見る</summary>

- 差: 1.0ポイント（相対的に約22%の改善）
- 統計的検定が必要だが、サンプルサイズが大きければ有意になりうる
- **実務判断**: 1%の改善でも、アクセス数が多いサイトでは大きな収益差になりうる

**答え: 統計的検定の結果次第だが、実務的には検討に値する差**

</details>

### Q6-4: サンプルサイズ <span class="difficulty-badge difficulty-2">標準</span>

信頼区間の幅を半分にしたい場合、サンプルサイズは何倍必要ですか？

<details markdown="1">
<summary>解答を見る</summary>

信頼区間の幅は $\frac{1}{\sqrt{n}}$ に比例する。

幅を半分にするには $\sqrt{n}$ を2倍に、つまり $n$ を4倍にする必要がある。

**答え: 4倍**

</details>

### Q6-5: 総合問題 <span class="difficulty-badge difficulty-3">発展</span>

ある商品の満足度調査で、n=100、平均4.2点（5点満点）、標準偏差0.8点でした。母平均の95%信頼区間を求めてください。

<details markdown="1">
<summary>解答を見る</summary>

$$SE = \frac{0.8}{\sqrt{100}} = 0.08$$

$$95\%CI = 4.2 \pm 1.96 \times 0.08 = 4.2 \pm 0.157$$

**答え: 4.04点 から 4.36点**

</details>

---

## 次のステップ

クイックコースを終えたら:

1. **苦手分野を復習**: 間違えた問題の理論ページを再読
2. **追加問題に挑戦**: [問題編一覧]({{ site.baseurl }}/problems/)でより多くの問題を解く
3. **用語を確認**: [用語集]({{ site.baseurl }}/glossary/)で重要用語をチェック

---

[トップページに戻る]({{ site.baseurl }}/) | [問題編一覧]({{ site.baseurl }}/problems/)
