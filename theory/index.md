---
layout: default
title: 理論編 - Stats Sensei
---

# 理論編

統計学の基礎から応用まで、体系的に学習できるコンテンツを用意しています。

---

## 記事一覧

{% for item in site.theory %}
- [{{ item.title }}]({{ item.url | relative_url }})
{% endfor %}

---

## カテゴリ別目次

### 記述統計

データの特徴を数値やグラフで要約する方法を学びます。

- [平均・中央値・最頻値]({{ site.baseurl }}/theory/mean-median-mode/)
- [分散と標準偏差]({{ site.baseurl }}/theory/variance-std/)
- [ヒストグラムと度数分布]({{ site.baseurl }}/theory/histogram/)

### 確率の基礎

統計学の土台となる確率論の基礎を学びます。

- [確率の基本概念]({{ site.baseurl }}/theory/probability-basics/)
- [条件付き確率とベイズの定理]({{ site.baseurl }}/theory/conditional-probability/)
- [確率変数と期待値]({{ site.baseurl }}/theory/expected-value/)

### 確率分布

データの分布を表現するための確率分布を学びます。

- [二項分布]({{ site.baseurl }}/theory/binomial/)
- [ポアソン分布]({{ site.baseurl }}/theory/poisson/)
- [正規分布]({{ site.baseurl }}/theory/normal-distribution/)

### 推定と検定

サンプルデータから母集団の特性を推測する方法を学びます。

- [区間推定]({{ site.baseurl }}/theory/interval-estimation/)
- [仮説検定の基礎]({{ site.baseurl }}/theory/hypothesis-testing/)
- [t検定]({{ site.baseurl }}/theory/t-test/)

### 回帰分析

変数間の関係を分析する方法を学びます。

- [相関分析]({{ site.baseurl }}/theory/correlation/)
- [単回帰分析]({{ site.baseurl }}/theory/regression/)
- [重回帰分析]({{ site.baseurl }}/theory/multiple-regression/)

---

[トップページに戻る]({{ site.baseurl }}/)
