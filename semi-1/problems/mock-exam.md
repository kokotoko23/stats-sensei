---
layout: default
title: 模擬試験モード - 準1級対策
description: 統計検定準1級の模擬試験。制限時間付きでランダム出題。
permalink: /semi-1/problems/mock-exam/
---

# 模擬試験モード

本番に近い形式で実力を試しましょう。全9分野からランダムに問題が出題されます。

<div id="mock-exam-setup" class="mock-exam-setup">
  <h2>試験設定</h2>
  <p>問題数と制限時間を選択してください</p>

  <div class="mock-exam-options" id="question-count-options">
    <div class="mock-exam-option" data-value="10">
      <div class="option-title">10問</div>
      <div class="option-desc">15分・お手軽</div>
    </div>
    <div class="mock-exam-option selected" data-value="20">
      <div class="option-title">20問</div>
      <div class="option-desc">30分・標準</div>
    </div>
    <div class="mock-exam-option" data-value="30">
      <div class="option-title">30問</div>
      <div class="option-desc">45分・本格</div>
    </div>
  </div>

  <button class="mock-exam-start" id="start-exam">試験開始</button>
</div>

<div id="mock-exam-timer" class="mock-exam-timer">
  <div class="timer-label">残り時間</div>
  <div class="timer-value" id="timer-display">30:00</div>
</div>

<div id="mock-exam-progress" class="mock-exam-progress">
  <div class="progress-label">進捗</div>
  <div class="progress-value" id="progress-display">0/20</div>
</div>

<div id="mock-exam-questions" style="display: none;">
  <div id="question-nav" class="mock-exam-question-nav"></div>
  <div id="questions-container"></div>
</div>

<div id="mock-exam-submit" class="mock-exam-submit">
  <button id="submit-exam">試験を終了する</button>
</div>

<div id="mock-exam-results" class="mock-exam-results">
  <h2>試験結果</h2>
  <div class="result-score" id="result-score">0%</div>
  <div class="result-detail" id="result-detail">0問中0問正解</div>
  <div class="result-time" id="result-time">所要時間: 00:00</div>
  <div style="margin-top: 24px;">
    <button class="mock-exam-start" onclick="location.reload()">もう一度挑戦</button>
  </div>
  <div id="result-breakdown" style="margin-top: 32px; text-align: left;"></div>
</div>

<script>
// 問題データベース（各分野から取得）
const questionDatabase = {
  probability: [
    { id: 'prob-1', question: '事象 $A$ と $B$ が独立であるとき、$P(A \\cup B)$ を $P(A) = p$、$P(B) = q$ を用いて表すとどれか。', options: ['$p + q$', '$pq$', '$p + q - pq$', '$1 - (1-p)(1-q)$'], correct: 2, difficulty: 'easy', category: '確率論' },
    { id: 'prob-2', question: '有病率1%、感度95%、特異度90%の検査で陽性と判定された人が実際に病気である確率に最も近いものはどれか。', options: ['約5%', '約9%', '約50%', '約95%'], correct: 1, difficulty: 'medium', category: '確率論' },
    { id: 'prob-3', question: 'MGFが $M_X(t) = e^{3t + 2t^2}$ のとき、$E[X]$ と $\\text{Var}(X)$ の値はどれか。', options: ['$E[X] = 3$、$\\text{Var}(X) = 4$', '$E[X] = 3$、$\\text{Var}(X) = 2$', '$E[X] = 2$、$\\text{Var}(X) = 3$', '$E[X] = 5$、$\\text{Var}(X) = 4$'], correct: 0, difficulty: 'medium', category: '確率論' },
    { id: 'prob-6', question: 'チェビシェフの不等式 $P(|X - \\mu| \\geq k\\sigma) \\leq ?$ の右辺はどれか。', options: ['$k$', '$1/k^2$', '$1/k$', '$\\sigma^2/k^2$'], correct: 1, difficulty: 'easy', category: '確率論' },
    { id: 'prob-7', question: '全期待値の法則の正しい表現はどれか。', options: ['$E[X] = E[E[X \\mid Y]]$', '$E[X] = E[X \\mid E[Y]]$', '$E[X \\mid Y] = E[X] \\cdot E[Y]$', '$E[X] = E[Y \\mid X]$'], correct: 0, difficulty: 'medium', category: '確率論' }
  ],
  distributions: [
    { id: 'dist-1', question: '$X \\sim N(0,1)$ のとき、$X^2$ の分布はどれか。', options: ['$N(0, 1)$', '$\\chi^2(1)$', '$t(1)$', '$F(1, 1)$'], correct: 1, difficulty: 'easy', category: '確率分布' },
    { id: 'dist-2', question: '中心極限定理で、標本平均の分布が正規分布に収束するために必要な条件はどれか。', options: ['母集団が正規分布に従う', '分散が有限である', '標本サイズが30以上', '独立同分布である'], correct: 0, difficulty: 'medium', category: '確率分布' },
    { id: 'dist-3', question: '$X_1, \\ldots, X_n \\sim N(\\mu, \\sigma^2)$ のとき、$(n-1)S^2/\\sigma^2$ の分布はどれか。', options: ['$\\chi^2(n)$', '$\\chi^2(n-1)$', '$t(n-1)$', '$F(n-1, n-1)$'], correct: 2, difficulty: 'medium', category: '確率分布' },
    { id: 'dist-6', question: 't分布の定義として正しいものはどれか。', options: ['$Z/\\sqrt{V/n}$（$Z \\sim N(0,1)$, $V \\sim \\chi^2(n)$、独立）', '$V_1/V_2$（$V_i \\sim \\chi^2(n_i)$、独立）', '$Z^2$（$Z \\sim N(0,1)$）', '$\\sum Z_i^2$（$Z_i \\sim N(0,1)$、独立）'], correct: 0, difficulty: 'easy', category: '確率分布' },
    { id: 'dist-8', question: '負の二項分布 $NB(r, p)$ の平均はどれか。', options: ['$rp$', '$r/p$', '$r(1-p)/p$', '$(1-p)/p$'], correct: 2, difficulty: 'hard', category: '確率分布' }
  ],
  stochastic: [
    { id: 'stoch-1', question: 'マルコフ連鎖の「マルコフ性」を正しく表しているものはどれか。', options: ['$P(X_{n+1} = j) = P(X_n = j)$', '$P(X_{n+1} = j \\mid X_0, \\ldots, X_n) = P(X_{n+1} = j)$', '$P(X_{n+1} = j \\mid X_0, \\ldots, X_n) = P(X_{n+1} = j \\mid X_n)$', '$P(X_{n+1} = j \\mid X_n = i) = P(X_1 = j \\mid X_0 = i)$'], correct: 2, difficulty: 'easy', category: '確率過程' },
    { id: 'stoch-3', question: 'ポアソン過程 $N(t)$ と $N(s+t) - N(s)$ の分布について正しいものはどれか。', options: ['$N(t) \\sim \\text{Poi}(\\lambda)$', '$N(t) \\sim \\text{Poi}(\\lambda t)$、$N(s+t) - N(s) \\sim \\text{Poi}(\\lambda t)$', '$N(t) \\sim \\text{Poi}(\\lambda t)$、$N(s+t) - N(s) \\sim \\text{Poi}(\\lambda s)$', '$N(t) \\sim \\text{Exp}(\\lambda t)$'], correct: 1, difficulty: 'easy', category: '確率過程' },
    { id: 'stoch-4', question: 'ポアソン過程の到着間隔 $T$ の分布はどれか。', options: ['$\\text{Poi}(\\lambda)$', '$\\text{Gamma}(2, \\lambda)$', '$U(0, 1/\\lambda)$', '$\\text{Exp}(\\lambda)$'], correct: 3, difficulty: 'easy', category: '確率過程' },
    { id: 'stoch-5', question: '有限状態マルコフ連鎖がエルゴード的であるための条件はどれか。', options: ['すべての推移確率が正', '可約である', '既約かつ非周期的', '周期的である'], correct: 2, difficulty: 'medium', category: '確率過程' },
    { id: 'stoch-10', question: 'マルチンゲールの条件として正しいものはどれか。', options: ['$E[M_{n+1} \\mid M_0, \\ldots, M_n] = M_0$', '$E[M_{n+1} \\mid M_0, \\ldots, M_n] = M_n$', '$E[M_{n+1} \\mid M_0, \\ldots, M_n] > M_n$', '$E[M_{n+1}] = E[M_n] + 1$'], correct: 1, difficulty: 'hard', category: '確率過程' }
  ],
  estimation: [
    { id: 'est-1', question: 'MLEの性質として正しくないものはどれか。', options: ['一致性', '漸近正規性', '不偏性（有限標本で常に成立）', '不変性'], correct: 2, difficulty: 'easy', category: '推定' },
    { id: 'est-2', question: 'ベルヌーイ分布 $\\text{Ber}(p)$ のフィッシャー情報量はどれか。', options: ['$1/p$', '$1/(p(1-p))$', '$p(1-p)$', '$1/p^2$'], correct: 1, difficulty: 'medium', category: '推定' },
    { id: 'est-4', question: '$X_1, \\ldots, X_n \\sim N(\\mu, 1)$ のクラメル・ラオ下界はどれか。', options: ['$1$', '$1/\\sqrt{n}$', '$1/n^2$', '$1/n$'], correct: 3, difficulty: 'medium', category: '推定' },
    { id: 'est-5', question: 'ポアソン分布の $\\lambda$ の最尤推定量はどれか。', options: ['$n/\\sum X_i$', '$\\sqrt{\\bar{X}}$', '$\\bar{X}$', '$\\sum X_i^2/n$'], correct: 2, difficulty: 'easy', category: '推定' },
    { id: 'est-10', question: '二乗損失のベイズ推定量はどれか。', options: ['事後平均', 'MAP推定量', '事後中央値', '最尤推定量'], correct: 0, difficulty: 'hard', category: '推定' }
  ],
  testing: [
    { id: 'test-1', question: '第一種の過誤（Type I error）の定義はどれか。', options: ['対立仮説が真のとき帰無仮説を棄却しない', '帰無仮説が真のとき帰無仮説を棄却する', '対立仮説が真のとき帰無仮説を棄却する', '帰無仮説が真のとき帰無仮説を棄却しない'], correct: 1, difficulty: 'easy', category: '検定' },
    { id: 'test-2', question: '尤度比検定統計量 $\\Lambda$ の定義として正しいものはどれか。', options: ['$L(\\hat{\\theta})/L(\\theta_0)$', '$L(\\theta_0)/L(\\hat{\\theta})$', '$\\log L(\\hat{\\theta}) - \\log L(\\theta_0)$', '$2[\\log L(\\hat{\\theta}) - \\log L(\\theta_0)]$'], correct: 1, difficulty: 'medium', category: '検定' },
    { id: 'test-4', question: 'p値の定義として正しいものはどれか。', options: ['帰無仮説が真である確率', '対立仮説が真である確率', '検定統計量が観測値以上に極端な値をとる確率', '第二種の過誤を犯す確率'], correct: 2, difficulty: 'easy', category: '検定' },
    { id: 'test-6', question: '検定の検出力（power）の定義はどれか。', options: ['対立仮説が真のとき帰無仮説を棄却する確率', '帰無仮説が真のとき帰無仮説を棄却しない確率', '第一種の過誤の確率', '帰無仮説が真のとき帰無仮説を棄却する確率'], correct: 0, difficulty: 'medium', category: '検定' },
    { id: 'test-9', question: 'FDR（偽発見率）制御で用いられる方法はどれか。', options: ['ボンフェローニ補正', 'ベンジャミニ・ホッホベルグ法', 'シダック補正', 'ホルム法'], correct: 1, difficulty: 'hard', category: '検定' }
  ],
  design: [
    { id: 'design-1', question: '乱塊法（RBD）の主な目的はどれか。', options: ['ブロック間のばらつきを制御', '交互作用を検出', '系統誤差を除去', '多重比較を行う'], correct: 0, difficulty: 'easy', category: '実験計画' },
    { id: 'design-2', question: '2元配置分散分析で検出できないものはどれか。', options: ['因子Aの主効果', '因子Bの主効果', '交互作用', '3次の交互作用'], correct: 2, difficulty: 'medium', category: '実験計画' },
    { id: 'design-4', question: '層化抽出法の利点はどれか。', options: ['実施が容易', '各層の特性を反映した推定が可能', '無作為抽出が不要', '標本サイズを小さくできる'], correct: 1, difficulty: 'easy', category: '実験計画' },
    { id: 'design-6', question: 'ラテン方格法で制御できるブロック因子の数はどれか。', options: ['0個', '1個', '2個', '3個'], correct: 2, difficulty: 'hard', category: '実験計画' },
    { id: 'design-9', question: '系統抽出法の特徴として正しいものはどれか。', options: ['完全に無作為', '周期性があると偏りが生じる可能性', '層化抽出より常に優れる', '母集団リストが不要'], correct: 1, difficulty: 'easy', category: '実験計画' }
  ],
  regression: [
    { id: 'reg-1', question: '最小二乗法の推定量 $\\hat{\\beta}$ を不偏にする条件はどれか。', options: ['誤差項が正規分布', '$E[\\varepsilon] = 0$', '誤差項が等分散', '説明変数が確率変数でない'], correct: 1, difficulty: 'easy', category: '回帰分析' },
    { id: 'reg-2', question: '決定係数 $R^2$ について正しいものはどれか。', options: ['負の値をとりうる', '説明変数を増やすと必ず増加', '0から1の値をとる', '因果関係を示す'], correct: 3, difficulty: 'medium', category: '回帰分析' },
    { id: 'reg-4', question: 'VIF（分散拡大係数）が10以上のとき懸念される問題はどれか。', options: ['不均一分散', '系列相関', '外れ値', '多重共線性'], correct: 0, difficulty: 'easy', category: '回帰分析' },
    { id: 'reg-6', question: 'LASSOの正則化項はどれか。', options: ['$\\lambda \\sum |\\beta_j|$', '$\\lambda \\sum \\beta_j^2$', '$\\lambda \\sum |\\beta_j|^{1/2}$', '$\\lambda \\max |\\beta_j|$'], correct: 2, difficulty: 'hard', category: '回帰分析' },
    { id: 'reg-9', question: 'ポアソン回帰のリンク関数はどれか。', options: ['恒等関数', 'ロジット関数', '対数関数', 'プロビット関数'], correct: 2, difficulty: 'hard', category: '回帰分析' }
  ],
  multivariate: [
    { id: 'mv-1', question: '主成分分析の目的はどれか。', options: ['変数間の因果関係を推定', '次元削減と情報の要約', 'グループ間の差異を最大化', 'クラスターの発見'], correct: 1, difficulty: 'easy', category: '多変量解析' },
    { id: 'mv-2', question: '主成分の固有値が表すものはどれか。', options: ['元の変数の分散', '主成分が説明する分散', '主成分間の相関', '標準化係数'], correct: 2, difficulty: 'medium', category: '多変量解析' },
    { id: 'mv-4', question: '判別分析の目的はどれか。', options: ['変数の次元削減', '潜在因子の発見', 'グループへの分類', 'クラスターの形成'], correct: 2, difficulty: 'easy', category: '多変量解析' },
    { id: 'mv-5', question: 'k-means法の特徴として正しいものはどれか。', options: ['階層的クラスタリング', 'クラスター数を事前に指定', '樹形図を出力', 'クラスター数を自動決定'], correct: 1, difficulty: 'medium', category: '多変量解析' },
    { id: 'mv-7', question: '多次元尺度構成法（MDS）の主な目的はどれか。', options: ['変数間の因果関係推定', '類似度データの可視化', 'グループ分類', '次元の独立性検定'], correct: 1, difficulty: 'hard', category: '多変量解析' }
  ],
  advanced: [
    { id: 'adv-1', question: 'ARIMA(p,d,q)モデルの d は何を表すか。', options: ['AR次数', '差分の階数', 'MA次数', '季節周期'], correct: 2, difficulty: 'medium', category: '発展的手法' },
    { id: 'adv-4', question: 'AICを最小化する意味はどれか。', options: ['過学習を防ぎつつ当てはまりを良くする', '計算量を減らす', '解釈を容易にする', '外れ値の影響を減らす'], correct: 0, difficulty: 'medium', category: '発展的手法' },
    { id: 'adv-6', question: 'Leave-One-Out交差検証の特徴はどれか。', options: ['計算が高速', '分散が小さい', 'ほぼ不偏だが分散が大きい', 'データ数によらず5分割'], correct: 2, difficulty: 'medium', category: '発展的手法' },
    { id: 'adv-7', question: 'MCMCの主な用途はどれか。', options: ['最尤推定', '事後分布からのサンプリング', '仮説検定', '主成分分析'], correct: 1, difficulty: 'hard', category: '発展的手法' },
    { id: 'adv-9', question: 'モンテカルロ積分で推定されるものはどれか。', options: ['最大値', '期待値（積分）', '分散', 'モード'], correct: 1, difficulty: 'hard', category: '発展的手法' }
  ]
};

// グローバル変数
let examState = {
  questions: [],
  answers: {},
  startTime: null,
  timeLimit: 30 * 60, // 秒
  timerInterval: null,
  questionCount: 20
};

// 初期化
document.addEventListener('DOMContentLoaded', function() {
  // 問題数選択
  document.querySelectorAll('#question-count-options .mock-exam-option').forEach(opt => {
    opt.addEventListener('click', function() {
      document.querySelectorAll('#question-count-options .mock-exam-option').forEach(o => o.classList.remove('selected'));
      this.classList.add('selected');
      examState.questionCount = parseInt(this.dataset.value);
      examState.timeLimit = examState.questionCount * 90; // 1問90秒
    });
  });

  // 試験開始
  document.getElementById('start-exam').addEventListener('click', startExam);

  // 試験終了
  document.getElementById('submit-exam').addEventListener('click', submitExam);
});

function startExam() {
  // 問題をシャッフルして選択
  examState.questions = selectRandomQuestions(examState.questionCount);
  examState.answers = {};
  examState.startTime = Date.now();

  // UIを更新
  document.getElementById('mock-exam-setup').style.display = 'none';
  document.getElementById('mock-exam-questions').style.display = 'block';
  document.getElementById('mock-exam-timer').classList.add('active');
  document.getElementById('mock-exam-progress').classList.add('active');
  document.getElementById('mock-exam-submit').classList.add('active');

  // 問題を表示
  renderQuestions();
  renderQuestionNav();
  updateProgress();

  // タイマー開始
  startTimer();

  // MathJaxを再レンダリング
  if (window.MathJax) {
    MathJax.typesetPromise();
  }
}

function selectRandomQuestions(count) {
  const allQuestions = [];
  Object.keys(questionDatabase).forEach(category => {
    questionDatabase[category].forEach(q => {
      allQuestions.push({ ...q, categoryKey: category });
    });
  });

  // シャッフル
  for (let i = allQuestions.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [allQuestions[i], allQuestions[j]] = [allQuestions[j], allQuestions[i]];
  }

  return allQuestions.slice(0, count);
}

function renderQuestions() {
  const container = document.getElementById('questions-container');
  container.innerHTML = '';
  const difficultyLabels = {easy: '基礎', medium: '標準', hard: '発展'};

  examState.questions.forEach((q, index) => {
    const optionsHtml = q.options.map((opt, i) => `
      <div class="quiz-option" data-value="${i}" onclick="selectAnswer(${index}, ${i})">
        <input type="radio" name="q${index}" id="q${index}o${i}">
        <label for="q${index}o${i}">${opt}</label>
      </div>
    `).join('');

    const diffLabel = difficultyLabels[q.difficulty];
    const questionHtml = `
      <div class="quiz-container" id="question-${index}" data-difficulty="${q.difficulty}">
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px;">
          <span style="font-weight: 600; color: #666;">問題 ${index + 1} / ${examState.questions.length}</span>
          <span class="difficulty-tag">${diffLabel}</span>
        </div>
        <div class="quiz-question">${q.question}</div>
        <div class="quiz-options">${optionsHtml}</div>
      </div>
      <hr>
    `;
    container.innerHTML += questionHtml;
  });
}

function renderQuestionNav() {
  const nav = document.getElementById('question-nav');
  nav.innerHTML = '';

  examState.questions.forEach((q, index) => {
    const item = document.createElement('div');
    item.className = 'nav-item';
    item.textContent = index + 1;
    item.onclick = () => scrollToQuestion(index);
    nav.appendChild(item);
  });
}

function scrollToQuestion(index) {
  const element = document.getElementById(`question-${index}`);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth', block: 'center' });
  }
  updateQuestionNavCurrent(index);
}

function updateQuestionNavCurrent(index) {
  document.querySelectorAll('.mock-exam-question-nav .nav-item').forEach((item, i) => {
    item.classList.toggle('current', i === index);
  });
}

function selectAnswer(questionIndex, optionIndex) {
  examState.answers[questionIndex] = optionIndex;

  // 選択状態を更新
  const container = document.getElementById(`question-${questionIndex}`);
  container.querySelectorAll('.quiz-option').forEach((opt, i) => {
    opt.classList.toggle('selected', i === optionIndex);
    opt.querySelector('input').checked = i === optionIndex;
  });

  // ナビを更新
  document.querySelectorAll('.mock-exam-question-nav .nav-item')[questionIndex].classList.add('answered');

  updateProgress();
}

function updateProgress() {
  const answered = Object.keys(examState.answers).length;
  document.getElementById('progress-display').textContent = `${answered}/${examState.questions.length}`;
}

function startTimer() {
  let remaining = examState.timeLimit;

  const updateDisplay = () => {
    const minutes = Math.floor(remaining / 60);
    const seconds = remaining % 60;
    document.getElementById('timer-display').textContent =
      `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;

    const timer = document.getElementById('mock-exam-timer');
    timer.classList.remove('warning', 'danger');
    if (remaining <= 60) {
      timer.classList.add('danger');
    } else if (remaining <= 300) {
      timer.classList.add('warning');
    }

    if (remaining <= 0) {
      submitExam();
    }
    remaining--;
  };

  updateDisplay();
  examState.timerInterval = setInterval(updateDisplay, 1000);
}

function submitExam() {
  clearInterval(examState.timerInterval);

  const endTime = Date.now();
  const elapsedSeconds = Math.floor((endTime - examState.startTime) / 1000);

  // 採点
  let correct = 0;
  const categoryResults = {};
  const questionResults = [];

  examState.questions.forEach((q, index) => {
    const userAnswer = examState.answers[index];
    const isCorrect = userAnswer === q.correct;
    if (isCorrect) correct++;

    if (!categoryResults[q.category]) {
      categoryResults[q.category] = { correct: 0, total: 0 };
    }
    categoryResults[q.category].total++;
    if (isCorrect) categoryResults[q.category].correct++;

    questionResults.push({
      index: index,
      question: q.question,
      options: q.options,
      userAnswer: userAnswer,
      correctAnswer: q.correct,
      isCorrect: isCorrect,
      category: q.category,
      difficulty: q.difficulty
    });
  });

  const score = Math.round((correct / examState.questions.length) * 100);

  // 結果を表示
  document.getElementById('mock-exam-questions').style.display = 'none';
  document.getElementById('mock-exam-timer').classList.remove('active');
  document.getElementById('mock-exam-progress').classList.remove('active');
  document.getElementById('mock-exam-submit').classList.remove('active');
  document.getElementById('mock-exam-results').classList.add('active');

  document.getElementById('result-score').textContent = score + '%';
  document.getElementById('result-detail').textContent = examState.questions.length + '問中' + correct + '問正解';

  const minutes = Math.floor(elapsedSeconds / 60);
  const seconds = elapsedSeconds % 60;
  document.getElementById('result-time').textContent =
    '所要時間: ' + minutes + '分' + seconds + '秒';

  // 分野別結果
  let breakdownHtml = '<h3>分野別結果</h3><table><tr><th>分野</th><th>正解</th><th>正答率</th></tr>';
  Object.keys(categoryResults).forEach(cat => {
    const r = categoryResults[cat];
    const rate = Math.round((r.correct / r.total) * 100);
    breakdownHtml += '<tr><td>' + cat + '</td><td>' + r.correct + '/' + r.total + '</td><td>' + rate + '%</td></tr>';
  });
  breakdownHtml += '</table>';

  // 問題の振り返り
  const difficultyLabels = {easy: '基礎', medium: '標準', hard: '発展'};
  const optionLabels = ['(a)', '(b)', '(c)', '(d)'];

  breakdownHtml += '<h3 style="margin-top: 32px;">問題の振り返り</h3>';
  breakdownHtml += '<p style="color: #666; font-size: 14px;">各問題の正誤を確認できます。</p>';

  questionResults.forEach((result, idx) => {
    const statusClass = result.isCorrect ? 'correct' : 'incorrect';
    const statusIcon = result.isCorrect ? '○' : '×';
    const statusColor = result.isCorrect ? '#22c55e' : '#ef4444';

    breakdownHtml += '<div class="review-question" style="background: white; border: 2px solid ' + (result.isCorrect ? '#22c55e' : '#ef4444') + '; border-radius: 12px; padding: 20px; margin: 16px 0;">';
    breakdownHtml += '<div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px;">';
    breakdownHtml += '<span style="font-weight: 600;">問題 ' + (idx + 1) + ' <span style="color: ' + statusColor + '; font-size: 20px;">' + statusIcon + '</span></span>';
    breakdownHtml += '<span style="background: ' + (result.difficulty === 'easy' ? '#4CAF50' : result.difficulty === 'medium' ? '#FF9800' : '#F44336') + '; color: white; padding: 4px 12px; border-radius: 12px; font-size: 12px;">' + difficultyLabels[result.difficulty] + '</span>';
    breakdownHtml += '</div>';
    breakdownHtml += '<div style="font-weight: 500; margin-bottom: 16px;">' + result.question + '</div>';
    breakdownHtml += '<div style="display: flex; flex-direction: column; gap: 8px;">';

    result.options.forEach((opt, optIdx) => {
      let optStyle = 'padding: 10px 14px; border-radius: 6px; border: 1px solid #e0e0e0;';
      let prefix = '';

      if (optIdx === result.correctAnswer) {
        optStyle = 'padding: 10px 14px; border-radius: 6px; border: 2px solid #22c55e; background: #dcfce7;';
        prefix = '<strong style="color: #22c55e;">正解 → </strong>';
      }
      if (optIdx === result.userAnswer && !result.isCorrect) {
        optStyle = 'padding: 10px 14px; border-radius: 6px; border: 2px solid #ef4444; background: #fee2e2;';
        prefix = '<strong style="color: #ef4444;">あなたの回答 → </strong>';
      }
      if (optIdx === result.userAnswer && result.isCorrect) {
        prefix = '<strong style="color: #22c55e;">正解 → </strong>';
      }

      breakdownHtml += '<div style="' + optStyle + '">' + prefix + optionLabels[optIdx] + ' ' + opt + '</div>';
    });

    if (result.userAnswer === undefined) {
      breakdownHtml += '<div style="color: #999; font-style: italic; margin-top: 8px;">未回答</div>';
    }

    breakdownHtml += '</div></div>';
  });

  document.getElementById('result-breakdown').innerHTML = breakdownHtml;

  // MathJaxを再レンダリング
  if (window.MathJax) {
    MathJax.typesetPromise();
  }
}
</script>

---

## 模擬試験について

| 項目 | 内容 |
|-----|-----|
| 出題範囲 | 全9分野（確率論、確率分布、確率過程、推定、検定、実験計画、回帰分析、多変量解析、発展的手法） |
| 出題形式 | 4択問題（ランダム出題） |
| 難易度 | 基礎・標準・発展がバランスよく出題 |
| 採点 | 終了後に即時採点、分野別正答率を表示 |

---

[問題一覧に戻る]({{ site.baseurl }}/semi-1/problems/) | [準1級トップ]({{ site.baseurl }}/semi-1/)
