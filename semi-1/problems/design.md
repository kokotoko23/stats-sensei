---
layout: default
title: 実験計画・調査の問題 - 準1級対策
description: 分散分析、多重比較、標本調査法の選択式問題
permalink: /semi-1/problems/design/
---

# 実験計画・調査の問題

分散分析、多重比較、標本調査法に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 10 正解</span>
  <div class="quiz-progress-bar">
    <div class="quiz-progress-fill" style="width: 0%"></div>
  </div>
</div>

---

## 問題 1：一元配置分散分析

<div class="quiz-container" data-quiz-id="design-1" data-correct="a">
  <div class="quiz-question">
    一元配置分散分析において、帰無仮説 $H_0: \mu_1 = \mu_2 = \cdots = \mu_k$ の検定に用いる統計量はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q1" id="q1a">
      <label for="q1a">$\displaystyle F = \frac{\text{群間平均平方}}{\text{群内平均平方}}$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q1" id="q1b">
      <label for="q1b">$\displaystyle t = \frac{\bar{x}_1 - \bar{x}_2}{s_p\sqrt{1/n_1 + 1/n_2}}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q1" id="q1c">
      <label for="q1c">$\displaystyle \chi^2 = \sum \frac{(O - E)^2}{E}$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q1" id="q1d">
      <label for="q1d">$\displaystyle z = \frac{\bar{x} - \mu}{\sigma/\sqrt{n}}$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      一元配置ANOVAでは $F$ 統計量を使用：

      $F = \frac{MS_B}{MS_W} = \frac{SS_B / (k-1)}{SS_W / (N-k)}$

      - $SS_B$：群間変動（群平均のばらつき）
      - $SS_W$：群内変動（各群内のばらつき）

      $H_0$ のもとで $F \sim F_{k-1, N-k}$。
    </div>
  </div>
</div>

---

## 問題 2：二元配置分散分析

<div class="quiz-container" data-quiz-id="design-2" data-correct="c">
  <div class="quiz-question">
    二元配置分散分析（繰り返しあり）で検定できる効果として<strong>含まれないもの</strong>はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q2" id="q2a">
      <label for="q2a">因子Aの主効果</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q2" id="q2b">
      <label for="q2b">因子Bの主効果</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q2" id="q2c">
      <label for="q2c">因子A×因子B×因子Cの三次交互作用</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q2" id="q2d">
      <label for="q2d">因子A×因子Bの交互作用</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      二元配置分散分析では2つの因子（A, B）を扱います。

      検定可能な効果：
      - 因子Aの主効果
      - 因子Bの主効果
      - 因子A×因子Bの交互作用

      三次交互作用（A×B×C）は3因子以上を含む設計でのみ検定可能です。
    </div>
  </div>
</div>

---

## 問題 3：多重比較

<div class="quiz-container" data-quiz-id="design-3" data-correct="b">
  <div class="quiz-question">
    Tukey法（HSD法）の特徴として正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q3" id="q3a">
      <label for="q3a">対照群との比較のみに使用される</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q3" id="q3b">
      <label for="q3b">すべてのペアワイズ比較に適している</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q3" id="q3c">
      <label for="q3c">群ごとにサンプルサイズが異なる場合のみ使用可能</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q3" id="q3d">
      <label for="q3d">FWERを制御しない</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      多重比較法の使い分け：

      - **Tukey法**：すべてのペアワイズ比較（$k$ 群から2群選ぶ全組み合わせ）
      - **Dunnett法**：対照群と各処理群の比較のみ
      - **Scheffé法**：任意の対比（最も保守的）
      - **Bonferroni法**：汎用的だが保守的

      Tukey法は等サンプルサイズで最も検出力が高く、FWERを $\alpha$ に制御します。
    </div>
  </div>
</div>

---

## 問題 4：層化抽出法

<div class="quiz-container" data-quiz-id="design-4" data-correct="d">
  <div class="quiz-question">
    層化抽出法について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q4" id="q4a">
      <label for="q4a">層内の分散が大きいほど効率的になる</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q4" id="q4b">
      <label for="q4b">層間の分散が小さいほど効率的になる</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q4" id="q4c">
      <label for="q4c">各層から同数のサンプルを抽出する方法のみを指す</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q4" id="q4d">
      <label for="q4d">層内が均質で層間が異質なとき、単純無作為抽出より効率的</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      層化抽出法の効率性：

      - **効率的な条件**：層内が均質（分散小）、層間が異質（分散大）
      - 各層から確実にサンプルを得られる
      - 層ごとの推定も可能

      配分方法：
      - 比例配分：層のサイズに比例
      - ネイマン配分：層のサイズ×標準偏差に比例（最適配分）
    </div>
  </div>
</div>

---

## 問題 5：クラスター抽出法

<div class="quiz-container" data-quiz-id="design-5" data-correct="a">
  <div class="quiz-question">
    クラスター抽出法（集落抽出法）と層化抽出法の違いについて正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q5" id="q5a">
      <label for="q5a">クラスター抽出では選ばれたクラスター内の全員（または一部）を調査する</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q5" id="q5b">
      <label for="q5b">層化抽出では一部の層のみから抽出する</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q5" id="q5c">
      <label for="q5c">クラスター内が異質なほど効率が下がる</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q5" id="q5d">
      <label for="q5d">両者は同じ手法の別名である</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      | 特徴 | 層化抽出 | クラスター抽出 |
      |-----|---------|--------------|
      | 抽出単位 | 全層から抽出 | 一部のクラスターを選択 |
      | 効率的な条件 | 層内均質、層間異質 | クラスター内異質、クラスター間均質 |
      | コスト | 高い（全層にアクセス必要） | 低い（選ばれたクラスターのみ） |

      クラスター抽出は地理的に分散した調査でコストを下げるために使用されます。
    </div>
  </div>
</div>

---

## 問題 6：ラテン方格法

<div class="quiz-container" data-quiz-id="design-6" data-correct="b">
  <div class="quiz-question">
    ラテン方格法の特徴として正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q6" id="q6a">
      <label for="q6a">3因子以上の交互作用を検定できる</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q6" id="q6b">
      <label for="q6b">行と列の2つのブロック因子を制御しながら処理効果を検定できる</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q6" id="q6c">
      <label for="q6c">完全無作為化法より必ず効率が低い</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q6" id="q6d">
      <label for="q6d">処理の水準数は自由に設定できる</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      ラテン方格法：$k \times k$ の格子に $k$ 種類の処理を、各行・各列に1回ずつ配置。

      特徴：
      - 2つのブロック因子（行・列）を制御
      - 処理数 = 行数 = 列数 が必要
      - 交互作用は検定できない（誤差と交絡）

      農業試験での畑の位置効果の制御などに使用。
    </div>
  </div>
</div>

---

## 問題 7：反復測定

<div class="quiz-container" data-quiz-id="design-7" data-correct="c">
  <div class="quiz-question">
    反復測定分散分析で注意が必要な「球面性の仮定」とは何か。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q7" id="q7a">
      <label for="q7a">各時点での分散が等しいこと</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q7" id="q7b">
      <label for="q7b">データが正規分布に従うこと</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q7" id="q7c">
      <label for="q7c">任意の2時点間の差の分散が等しいこと</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q7" id="q7d">
      <label for="q7d">被験者間の分散が0であること</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      球面性（sphericity）の仮定：

      $\text{Var}(Y_i - Y_j) = \text{const.}$ for all $i \neq j$

      すべての時点ペアの差の分散が等しいという条件。

      違反した場合の対処：
      - Greenhouse-Geisser補正
      - Huynh-Feldt補正
      - 多変量検定（MANOVA）の使用
    </div>
  </div>
</div>

---

## 問題 8：系統抽出

<div class="quiz-container" data-quiz-id="design-8" data-correct="a">
  <div class="quiz-question">
    系統抽出（等間隔抽出）について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q8" id="q8a">
      <label for="q8a">最初の要素を無作為に選び、以後は一定間隔で抽出する</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q8" id="q8b">
      <label for="q8b">母集団の各要素が選ばれる確率が異なる</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q8" id="q8c">
      <label for="q8c">周期性のあるデータに対して最も効率的</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q8" id="q8d">
      <label for="q8d">単純無作為抽出と完全に同じ性質を持つ</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      系統抽出の手順（$N$ から $n$ を抽出、抽出間隔 $k = N/n$）：
      1. $1$ から $k$ の間で開始点を無作為に選択
      2. 以後、$k$ 間隔で抽出

      特徴：
      - 実施が容易
      - 母集団がランダムなら単純無作為抽出と同等
      - 周期性があると偏りが生じる（例：毎週月曜の売上だけ抽出）
    </div>
  </div>
</div>

---

## 問題 9：分散分析の仮定

<div class="quiz-container" data-quiz-id="design-9" data-correct="d">
  <div class="quiz-question">
    一元配置分散分析の仮定として<strong>正しくないもの</strong>はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q9" id="q9a">
      <label for="q9a">各群の母集団は正規分布に従う</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q9" id="q9b">
      <label for="q9b">各群の分散は等しい（等分散性）</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q9" id="q9c">
      <label for="q9c">観測値は互いに独立である</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q9" id="q9d">
      <label for="q9d">各群のサンプルサイズは等しくなければならない</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      ANOVAの3つの仮定：
      1. **正規性**：各群のデータが正規分布に従う
      2. **等分散性**：各群の分散が等しい
      3. **独立性**：観測値が互いに独立

      サンプルサイズは等しくなくてもよい（不均衡データ）が、等しい方が：
      - 検出力が高い
      - 等分散性の仮定違反に頑健

      Welch検定は等分散性の仮定を緩和したもの。
    </div>
  </div>
</div>

---

## 問題 10：二段抽出

<div class="quiz-container" data-quiz-id="design-10" data-correct="b">
  <div class="quiz-question">
    二段抽出法について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q10" id="q10a">
      <label for="q10a">一次抽出単位のすべての要素を調査する</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q10" id="q10b">
      <label for="q10b">選ばれた一次抽出単位から、さらに二次抽出単位を抽出する</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q10" id="q10c">
      <label for="q10c">単純無作為抽出より常に精度が高い</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q10" id="q10d">
      <label for="q10d">層化抽出と同じ方法である</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      二段抽出法：
      1. 一次抽出：クラスター（一次抽出単位）を抽出
      2. 二次抽出：選ばれたクラスター内から個体を抽出

      例：全国調査で
      - 一次：市町村を抽出
      - 二次：選ばれた市町村から世帯を抽出

      特徴：
      - クラスター抽出（全員調査）よりコストは上がるが精度向上
      - デザイン効果を考慮した分析が必要
    </div>
  </div>
</div>

---

## 関連コンテンツ

- [理論編：分散分析と実験計画]({{ site.baseurl }}/semi-1/6-design/anova/)
- [理論編：標本調査法]({{ site.baseurl }}/semi-1/6-design/sampling/)
- [検定の問題]({{ site.baseurl }}/semi-1/problems/testing/)

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
