---
layout: default
title: 実験計画・調査の問題 - 準1級対策
description: 分散分析、多重比較、標本調査法の選択式問題
permalink: /semi-1/problems/design/
---

# 実験計画・調査の問題

分散分析、多重比較、標本調査法に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 5 正解</span>
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

## 関連コンテンツ

- [理論編：分散分析と実験計画]({{ site.baseurl }}/semi-1/6-design/anova/)
- [理論編：標本調査法]({{ site.baseurl }}/semi-1/6-design/sampling/)
- [検定の問題]({{ site.baseurl }}/semi-1/problems/testing/)

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
