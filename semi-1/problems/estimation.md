---
layout: default
title: 推定の問題 - 準1級対策
description: 最尤推定、十分統計量、フィッシャー情報量の選択式問題
permalink: /semi-1/problems/estimation/
---

# 推定の問題

最尤推定、十分統計量、フィッシャー情報量、クラメル・ラオの不等式に関する問題です。

<div class="quiz-progress">
  <span class="quiz-progress-text">0 / 10 正解</span>
  <div class="quiz-progress-bar">
    <div class="quiz-progress-fill" style="width: 0%"></div>
  </div>
</div>

---

## 問題 1：最尤推定量の性質

<div class="quiz-container" data-quiz-id="est-1" data-correct="c" data-difficulty="easy">
  <div class="quiz-question">
    最尤推定量（MLE）の性質として<strong>正しくないもの</strong>はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q1" id="q1a">
      <label for="q1a">一致性：$n \to \infty$ で真の値に確率収束する</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q1" id="q1b">
      <label for="q1b">漸近正規性：$\sqrt{n}(\hat{\theta} - \theta)$ は正規分布に収束する</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q1" id="q1c">
      <label for="q1c">不偏性：有限標本で常に $E[\hat{\theta}] = \theta$ が成り立つ</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q1" id="q1d">
      <label for="q1d">不変性：$g(\theta)$ のMLEは $g(\hat{\theta})$ である</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      MLEは一般に有限標本では不偏ではありません。例えば、正規分布の分散のMLEは $\frac{1}{n}\sum(x_i - \bar{x})^2$ で、これは不偏ではなく $\frac{n-1}{n}\sigma^2$ が期待値です。MLEは「漸近的に」不偏ですが、有限標本では偏りを持つことがあります。
    </div>
  </div>
</div>

---

## 問題 2：フィッシャー情報量

<div class="quiz-container" data-quiz-id="est-2" data-correct="b" data-difficulty="medium">
  <div class="quiz-question">
    ベルヌーイ分布 $\text{Ber}(p)$ の1標本のフィッシャー情報量 $I(p)$ はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q2" id="q2a">
      <label for="q2a">$\displaystyle \frac{1}{p}$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q2" id="q2b">
      <label for="q2b">$\displaystyle \frac{1}{p(1-p)}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q2" id="q2c">
      <label for="q2c">$\displaystyle p(1-p)$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q2" id="q2d">
      <label for="q2d">$\displaystyle \frac{1}{p^2}$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      $\log f(x;p) = x\log p + (1-x)\log(1-p)$ より、スコア関数は $U = \frac{x-p}{p(1-p)}$。
      フィッシャー情報量は $I(p) = E[U^2] = \frac{E[(X-p)^2]}{p^2(1-p)^2} = \frac{p(1-p)}{p^2(1-p)^2} = \frac{1}{p(1-p)}$。

      または、$-E[\partial^2 \log f / \partial p^2] = \frac{1}{p} + \frac{1}{1-p} = \frac{1}{p(1-p)}$ からも導けます。
    </div>
  </div>
</div>

---

## 問題 3：十分統計量

<div class="quiz-container" data-quiz-id="est-3" data-correct="a" data-difficulty="medium">
  <div class="quiz-question">
    $X_1, \ldots, X_n$ が独立に指数分布 $\text{Exp}(\lambda)$ に従うとき、$\lambda$ に対する十分統計量はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q3" id="q3a">
      <label for="q3a">$\displaystyle \sum_{i=1}^n X_i$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q3" id="q3b">
      <label for="q3b">$\displaystyle \sum_{i=1}^n X_i^2$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q3" id="q3c">
      <label for="q3c">$\displaystyle X_{(1)} = \min(X_1, \ldots, X_n)$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q3" id="q3d">
      <label for="q3d">$\displaystyle X_{(n)} = \max(X_1, \ldots, X_n)$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      尤度関数は $L(\lambda) = \lambda^n \exp(-\lambda \sum x_i)$ と書けます。
      分解定理より、$g(T, \lambda) = \lambda^n \exp(-\lambda T)$（$T = \sum x_i$）と $h(\mathbf{x}) = 1$ に分解できるので、$\sum X_i$ が十分統計量です。

      指数型分布族では、自然パラメータに対応する統計量が十分統計量になります。
    </div>
  </div>
</div>

---

## 問題 4：クラメル・ラオの不等式

<div class="quiz-container" data-quiz-id="est-4" data-correct="d" data-difficulty="medium">
  <div class="quiz-question">
    $X_1, \ldots, X_n$ が独立に $N(\mu, 1)$ に従うとき、$\mu$ の不偏推定量の分散の下界（クラメル・ラオ下界）はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q4" id="q4a">
      <label for="q4a">$1$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q4" id="q4b">
      <label for="q4b">$\displaystyle \frac{1}{\sqrt{n}}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q4" id="q4c">
      <label for="q4c">$\displaystyle \frac{1}{n^2}$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q4" id="q4d">
      <label for="q4d">$\displaystyle \frac{1}{n}$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      $N(\mu, 1)$ の1標本のフィッシャー情報量は $I(\mu) = 1/\sigma^2 = 1$。

      $n$ 標本では $I_n(\mu) = nI(\mu) = n$。

      クラメル・ラオ下界は $\frac{1}{I_n(\mu)} = \frac{1}{n}$。

      標本平均 $\bar{X}$ は $\text{Var}(\bar{X}) = \frac{1}{n}$ でこの下界を達成するので、有効推定量です。
    </div>
  </div>
</div>

---

## 問題 5：最尤推定量の導出

<div class="quiz-container" data-quiz-id="est-5" data-correct="c" data-difficulty="easy">
  <div class="quiz-question">
    $X_1, \ldots, X_n$ が独立にポアソン分布 $\text{Poi}(\lambda)$ に従うとき、$\lambda$ の最尤推定量はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q5" id="q5a">
      <label for="q5a">$\displaystyle \frac{n}{\sum_{i=1}^n X_i}$</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q5" id="q5b">
      <label for="q5b">$\displaystyle \sqrt{\frac{1}{n}\sum_{i=1}^n X_i}$</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q5" id="q5c">
      <label for="q5c">$\displaystyle \bar{X} = \frac{1}{n}\sum_{i=1}^n X_i$</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q5" id="q5d">
      <label for="q5d">$\displaystyle \frac{1}{n}\sum_{i=1}^n X_i^2$</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      対数尤度関数は $\ell(\lambda) = \sum x_i \log\lambda - n\lambda - \sum\log(x_i!)$。

      $\frac{d\ell}{d\lambda} = \frac{\sum x_i}{\lambda} - n = 0$ を解くと、

      $\hat{\lambda}_{\text{MLE}} = \frac{\sum x_i}{n} = \bar{X}$。

      ポアソン分布では、標本平均が最尤推定量になります。これは期待値 $E[X] = \lambda$ のモーメント推定量と一致します。
    </div>
  </div>
</div>

---

## 問題 6：指数型分布族

<div class="quiz-container" data-quiz-id="est-6" data-correct="a" data-difficulty="hard">
  <div class="quiz-question">
    指数型分布族の確率密度関数の標準形 $f(x;\theta) = h(x)\exp(\eta(\theta) T(x) - A(\theta))$ において、$T(x)$ は何を表すか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q6" id="q6a">
      <label for="q6a">自然パラメータに対応する十分統計量</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q6" id="q6b">
      <label for="q6b">キュムラント母関数</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q6" id="q6c">
      <label for="q6c">フィッシャー情報量</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q6" id="q6d">
      <label for="q6d">正規化定数</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      指数型分布族の構成要素：

      - $\eta(\theta)$：自然パラメータ（natural parameter）
      - $T(x)$：十分統計量（sufficient statistic）
      - $A(\theta)$：対数分配関数（キュムラント母関数）
      - $h(x)$：基底測度

      重要な性質：
      - $E[T(X)] = A'(\eta)$
      - $\text{Var}(T(X)) = A''(\eta)$
      - $A(\eta)$ はフィッシャー情報量の計算にも使われる
    </div>
  </div>
</div>

---

## 問題 7：完備性

<div class="quiz-container" data-quiz-id="est-7" data-correct="c" data-difficulty="hard">
  <div class="quiz-question">
    統計量 $T$ が完備（complete）であることの定義として正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q7" id="q7a">
      <label for="q7a">$T$ がパラメータの十分統計量であること</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q7" id="q7b">
      <label for="q7b">$T$ の分散が最小であること</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q7" id="q7c">
      <label for="q7c">任意の $\theta$ で $E_\theta[g(T)] = 0$ ならば $g(T) = 0$ a.s. となること</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q7" id="q7d">
      <label for="q7d">$T$ が不偏推定量であること</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(c)</strong>
    <div class="quiz-explanation">
      完備性の定義：すべての $\theta$ で $E_\theta[g(T)] = 0$ ならば、$P_\theta(g(T) = 0) = 1$ となること。

      重要な定理：
      - **レーマン・シェッフェの定理**：完備十分統計量の関数である不偏推定量は、一様最小分散不偏推定量（UMVUE）

      指数型分布族は完備十分統計量を持つことが多く、UMVUE を見つけやすい。
    </div>
  </div>
</div>

---

## 問題 8：有効推定量

<div class="quiz-container" data-quiz-id="est-8" data-correct="b" data-difficulty="medium">
  <div class="quiz-question">
    推定量が有効（efficient）であるとは何を意味するか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q8" id="q8a">
      <label for="q8a">漸近的に正規分布に従う</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q8" id="q8b">
      <label for="q8b">クラメル・ラオ下界を達成する不偏推定量である</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q8" id="q8c">
      <label for="q8c">計算が効率的である</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q8" id="q8d">
      <label for="q8d">一致性を持つ</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(b)</strong>
    <div class="quiz-explanation">
      有効推定量（efficient estimator）：クラメル・ラオ下界を達成する不偏推定量。

      $$\text{Var}(\hat{\theta}) = \frac{1}{nI(\theta)}$$

      有効推定量が存在する条件：
      - スコア関数が $U = a(\theta)(T - \tau(\theta))$ の形に書ける
      - これは指数型分布族で成り立つ

      例：正規分布の平均の推定で標本平均は有効推定量。
    </div>
  </div>
</div>

---

## 問題 9：モーメント推定量

<div class="quiz-container" data-quiz-id="est-9" data-correct="d" data-difficulty="medium">
  <div class="quiz-question">
    モーメント法（積率法）による推定について正しいものはどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q9" id="q9a">
      <label for="q9a">常に最尤推定量と一致する</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q9" id="q9b">
      <label for="q9b">常に不偏推定量になる</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q9" id="q9c">
      <label for="q9c">常に有効推定量になる</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q9" id="q9d">
      <label for="q9d">計算が容易で、一致性を持つことが多い</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(d)</strong>
    <div class="quiz-explanation">
      モーメント法：母集団モーメント $E[X^k]$ を標本モーメント $\frac{1}{n}\sum X_i^k$ で置き換えてパラメータを推定。

      特徴：
      - 計算が容易（連立方程式を解くだけ）
      - 大数の法則により一致性を持つことが多い
      - 必ずしも最尤推定量と一致しない
      - 有効性は保証されない

      例：$\text{Gamma}(\alpha, \beta)$ では、MLEは反復計算が必要だがモーメント推定量は閉形式。
    </div>
  </div>
</div>

---

## 問題 10：ベイズ推定量

<div class="quiz-container" data-quiz-id="est-10" data-correct="a" data-difficulty="hard">
  <div class="quiz-question">
    二乗損失関数のもとでのベイズ推定量はどれか。
  </div>
  <div class="quiz-options">
    <div class="quiz-option" data-value="a">
      <input type="radio" name="q10" id="q10a">
      <label for="q10a">事後分布の期待値（事後平均）</label>
    </div>
    <div class="quiz-option" data-value="b">
      <input type="radio" name="q10" id="q10b">
      <label for="q10b">事後分布の最頻値（MAP推定量）</label>
    </div>
    <div class="quiz-option" data-value="c">
      <input type="radio" name="q10" id="q10c">
      <label for="q10c">事後分布の中央値</label>
    </div>
    <div class="quiz-option" data-value="d">
      <input type="radio" name="q10" id="q10d">
      <label for="q10d">最尤推定量</label>
    </div>
  </div>
  <button class="quiz-btn" disabled>解答を確認</button>
  <div class="quiz-feedback">
    <span class="quiz-feedback-icon"></span>
    <strong>正解：(a)</strong>
    <div class="quiz-explanation">
      損失関数とベイズ推定量の関係：

      | 損失関数 | ベイズ推定量 |
      |---------|------------|
      | 二乗損失 $(\theta - \hat{\theta})^2$ | 事後平均 |
      | 絶対損失 $|\theta - \hat{\theta}|$ | 事後中央値 |
      | 0-1損失 | 事後最頻値（MAP） |

      事後平均は、$E[(θ - \hat{θ})^2 \mid \mathbf{x}]$ を最小化する $\hat{θ}$ です。

      MAP推定量は、事前分布が一様のとき最尤推定量と一致します。
    </div>
  </div>
</div>

---

## 関連コンテンツ

- [理論編：推定の基礎]({{ site.baseurl }}/semi-1/3-inference/estimation/)
- [検定の問題]({{ site.baseurl }}/semi-1/problems/testing/)
- [信頼区間の問題]({{ site.baseurl }}/semi-1/problems/interval/)

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
