---
layout: default
title: Hosting Quiz - Find Your Perfect WordPress Host
description: Answer 5 quick questions and get a personalized hosting recommendation matched to your needs.
keywords: hosting quiz, find hosting, hosting recommendation, WordPress hosting selector
permalink: /quiz/
---

## Find Your Perfect WordPress Host

<div id="quiz-container" style="max-width: 700px; margin: 0 auto;">
  
  <!-- Progress Bar -->
  <div id="progress-bar" style="margin-bottom: 40px;">
    <div style="background: #e9ecef; border-radius: 10px; height: 8px; margin-bottom: 15px; overflow: hidden;">
      <div id="progress-fill" style="background: linear-gradient(90deg, #667eea 0%, #764ba2 100%); height: 100%; width: 0%; transition: width 0.3s ease;"></div>
    </div>
    <div style="display: flex; justify-content: space-between; align-items: center;">
      <span id="progress-text" style="font-weight: 600; color: #333; font-size: 0.95em;">Question 1 of 5</span>
      <span style="color: #999; font-size: 0.9em;">Takes ~2 minutes</span>
    </div>
  </div>

  <!-- Question Container -->
  <div id="quiz-question-container" style="background: white; border-radius: 12px; padding: 40px; box-shadow: 0 2px 10px rgba(0,0,0,0.08); margin-bottom: 30px;">
    <div id="current-question"></div>
  </div>

  <!-- Results Container -->
  <div id="quiz-results" style="display: none;">
    <div id="results-content"></div>
  </div>

</div>

<style>
.quiz-question-title {
  font-size: 1.8em;
  color: #333;
  margin: 0 0 30px 0;
  font-weight: 700;
  line-height: 1.4;
}

.quiz-option {
  margin: 15px 0;
}

.quiz-option input[type="radio"] {
  display: none;
}

.quiz-option label {
  display: block;
  padding: 18px 20px;
  background: #f9f9f9;
  border: 2px solid #e9ecef;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.2s ease;
  font-size: 1em;
  color: #333;
  font-weight: 500;
}

.quiz-option label:hover {
  background: #f0f4ff;
  border-color: #667eea;
}

.quiz-option input[type="radio"]:checked + label {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-color: #667eea;
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.3);
}

.quiz-button-group {
  display: flex;
  gap: 15px;
  margin-top: 40px;
  justify-content: space-between;
}

.btn {
  padding: 14px 30px;
  font-size: 1em;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s ease;
  min-width: 140px;
}

.btn-primary {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  flex-grow: 1;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(102, 126, 234, 0.4);
}

.btn-primary:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none;
}

.btn-secondary {
  background: #f0f0f0;
  color: #333;
}

.btn-secondary:hover {
  background: #e0e0e0;
}

.recommendation-card {
  background: white;
  border-radius: 12px;
  padding: 40px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.08);
}

.recommendation-header {
  text-align: center;
  margin-bottom: 40px;
}

.recommendation-header h2 {
  color: #333;
  font-size: 2em;
  margin-bottom: 15px;
}

.recommendation-tier-badge {
  display: inline-block;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 12px 25px;
  border-radius: 8px;
  font-size: 1.2em;
  font-weight: 700;
  margin: 20px 0;
}

.recommendation-explanation {
  background: #f0f8ff;
  padding: 25px;
  border-left: 4px solid #0066cc;
  border-radius: 8px;
  margin: 30px 0;
  color: #333;
  line-height: 1.8;
  font-size: 1.05em;
}

.provider-suggestion {
  background: #f9f9f9;
  border: 2px solid #e9ecef;
  border-radius: 8px;
  padding: 25px;
  margin: 20px 0;
  transition: all 0.3s ease;
}

.provider-suggestion:hover {
  border-color: #667eea;
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.1);
}

.provider-suggestion h4 {
  margin: 0 0 10px 0;
  color: #667eea;
  font-size: 1.2em;
}

.provider-price {
  font-weight: 700;
  color: #333;
  font-size: 1.1em;
  margin: 10px 0;
}

.provider-reason {
  color: #666;
  margin-top: 10px;
  line-height: 1.6;
}

.results-cta {
  margin-top: 40px;
  padding: 30px;
  background: linear-gradient(135deg, #f0f4ff 0%, #f8f9fa 100%);
  border-radius: 8px;
  text-align: center;
  border: 2px solid #e9ecef;
}

.results-cta p {
  color: #333;
  font-size: 1.05em;
  margin-bottom: 20px;
}

.results-cta a {
  display: inline-block;
  margin: 10px 10px;
  padding: 12px 25px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  text-decoration: none;
  border-radius: 6px;
  font-weight: 600;
  transition: all 0.3s ease;
}

.results-cta a:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(102, 126, 234, 0.3);
}

.take-again-btn {
  text-align: center;
  margin-top: 30px;
}
</style>

<script>
const quizData = {
  questions: [
    {
      id: 'revenue',
      question: 'Does your site generate revenue?',
      options: [
        { value: 'no', label: 'No – it\'s a hobby or portfolio site' },
        { value: 'yes-small', label: 'Yes – but revenue is under $10k/year' },
        { value: 'yes-medium', label: 'Yes – revenue is $10k-$100k/year' },
        { value: 'yes-high', label: 'Yes – revenue is over $100k/year' }
      ]
    },
    {
      id: 'traffic',
      question: 'How much monthly traffic do you expect?',
      options: [
        { value: 'low', label: 'Under 1,000 visitors/month' },
        { value: 'medium', label: '1,000-10,000 visitors/month' },
        { value: 'high', label: '10,000-100,000 visitors/month' },
        { value: 'very-high', label: 'Over 100,000 visitors/month' }
      ]
    },
    {
      id: 'technical',
      question: 'What\'s your technical comfort level?',
      options: [
        { value: 'none', label: 'Zero – I\'m non-technical' },
        { value: 'basic', label: 'Basic – I can Google and troubleshoot' },
        { value: 'intermediate', label: 'Intermediate – I\'m comfortable with servers' },
        { value: 'advanced', label: 'Advanced – Linux/command line is familiar' }
      ]
    },
    {
      id: 'setup',
      question: 'Do you need anything beyond WordPress?',
      options: [
        { value: 'just-wordpress', label: 'Just WordPress' },
        { value: 'wordpress-plus', label: 'WordPress + custom code/plugins' },
        { value: 'multiple', label: 'Multiple sites or platforms' }
      ]
    },
    {
      id: 'budget',
      question: 'What\'s your monthly hosting budget?',
      options: [
        { value: 'minimal', label: 'Under $10/month' },
        { value: 'moderate', label: '$10-30/month' },
        { value: 'comfortable', label: '$30-100/month' },
        { value: 'premium', label: 'Over $100/month' }
      ]
    }
  ],

  recommendations: {
    'no_low_none_just-wordpress_minimal': {
      tier: 'Shared Hosting',
      explanation: 'For hobby sites with minimal traffic, shared hosting is fine. You don\'t need premium features.',
      providers: [
        {
          name: 'Bluehost',
          price: '$2.95-4.95/month',
          reason: 'WordPress.org official recommendation. Easy for beginners, reliable for hobby sites.'
        },
        {
          name: 'Hostinger',
          price: '$2.99-3.99/month',
          reason: 'Good uptime, decent support. Balance of price and reliability.'
        }
      ],
      cta: 'Read our shared hosting guide for more options'
    },

    'yes-small_medium_basic_just-wordpress_moderate': {
      tier: 'Managed WordPress Hosting',
      explanation: 'Your site generates revenue and needs reliability. Managed hosting prevents costly downtime and performs well.',
      providers: [
        {
          name: 'Hostinger WordPress',
          price: '$9.99-19.99/month',
          reason: 'Great value for small business sites. Good support, WordPress-optimized.'
        },
        {
          name: 'Bluehost Pro',
          price: '$19.95+/month',
          reason: 'WordPress.org official. Better performance than shared. Good for growing sites.'
        },
        {
          name: 'SiteGround',
          price: '$2.99-7.99/month (promo)',
          reason: 'Excellent support, fast servers, WordPress-specialized.'
        }
      ],
      cta: 'Compare managed hosting providers side-by-side'
    },

    'yes-medium_high_basic_just-wordpress_moderate': {
      tier: 'Premium Managed WordPress Hosting',
      explanation: 'With growing traffic and revenue, you need fast, reliable hosting with expert support.',
      providers: [
        {
          name: 'Kinsta',
          price: '$35-100+/month',
          reason: 'Industry-leading performance. Fast servers, exceptional support, staging environments.'
        },
        {
          name: 'WP Engine',
          price: '$20-115+/month',
          reason: 'Enterprise-grade uptime. Best support team. Perfect for mission-critical sites.'
        },
        {
          name: 'Pressable',
          price: '$25-100+/month',
          reason: 'Automattic-owned (trusted). Very fast, great for content creators.'
        }
      ],
      cta: 'Read the complete guide to premium managed hosting'
    },

    'yes-high_high_intermediate_wordpress-plus_comfortable': {
      tier: 'Cloud Hosting / VPS',
      explanation: 'You have technical skills and need flexibility beyond what managed hosting offers.',
      providers: [
        {
          name: 'DigitalOcean',
          price: '$4-6+/month',
          reason: 'Simplest VPS interface. Great documentation. Minimal support but excellent for developers.'
        },
        {
          name: 'Linode',
          price: '$5-10+/month',
          reason: 'Similar to DigitalOcean with slightly better support. Very reliable.'
        },
        {
          name: 'Kinsta Cloud',
          price: '$50+/month',
          reason: 'If you want managed cloud with full control. Premium pricing for expert support.'
        }
      ],
      cta: 'Learn more about cloud hosting and VPS options'
    },

    'yes-high_very-high_advanced_multiple_premium': {
      tier: 'Enterprise Cloud Infrastructure',
      explanation: 'At your scale, you need full control and custom infrastructure. Consider consulting an expert.',
      providers: [
        {
          name: 'AWS / Google Cloud / Azure',
          price: '$50-500+/month',
          reason: 'Enterprise-grade. Complex but infinitely scalable.'
        },
        {
          name: 'Dedicated Server',
          price: '$80-300+/month',
          reason: 'Entire physical server is yours. Maximum control.'
        }
      ],
      cta: 'Read our advanced hosting guide for enterprise options'
    }
  },

  getKey: function(answers) {
    const keys = [
      answers.revenue,
      answers.traffic,
      answers.technical,
      answers.setup,
      answers.budget
    ];
    return keys.join('_');
  }
};

let currentAnswers = {};
let currentQuestion = 0;

function updateProgressBar() {
  const progress = ((currentQuestion + 1) / quizData.questions.length) * 100;
  document.getElementById('progress-fill').style.width = progress + '%';
  document.getElementById('progress-text').textContent = `Question ${currentQuestion + 1} of ${quizData.questions.length}`;
}

function renderQuestion() {
  const q = quizData.questions[currentQuestion];
  const isAnswered = currentAnswers[q.id] !== undefined;
  
  let html = `
    <h3 class="quiz-question-title">${q.question}</h3>
    <div>
      ${q.options.map(opt => `
        <div class="quiz-option">
          <input type="radio" id="${q.id}_${opt.value}" name="${q.id}" value="${opt.value}" ${currentAnswers[q.id] === opt.value ? 'checked' : ''} onchange="currentAnswers['${q.id}'] = '${opt.value}'; updateButton()">
          <label for="${q.id}_${opt.value}">${opt.label}</label>
        </div>
      `).join('')}
    </div>

    <div class="quiz-button-group">
      <button class="btn btn-secondary" onclick="previousQuestion()" style="display: ${currentQuestion === 0 ? 'none' : 'block'};">← Back</button>
      <button id="next-btn" class="btn btn-primary" onclick="nextQuestion()" ${isAnswered ? '' : 'disabled'}>
        ${currentQuestion === quizData.questions.length - 1 ? 'Get Recommendation' : 'Next →'}
      </button>
    </div>
  `;

  document.getElementById('current-question').innerHTML = html;
  updateProgressBar();
}

function updateButton() {
  const q = quizData.questions[currentQuestion];
  const btn = document.getElementById('next-btn');
  btn.disabled = !currentAnswers[q.id];
}

function nextQuestion() {
  const q = quizData.questions[currentQuestion];
  if (!currentAnswers[q.id]) {
    alert('Please select an answer before continuing.');
    return;
  }

  if (currentQuestion < quizData.questions.length - 1) {
    currentQuestion++;
    renderQuestion();
  } else {
    submitQuiz();
  }
}

function previousQuestion() {
  if (currentQuestion > 0) {
    currentQuestion--;
    renderQuestion();
  }
}

function submitQuiz() {
  // Try exact match first
  let key = quizData.getKey(currentAnswers);
  let rec = quizData.recommendations[key];

  // If no exact match, use fuzzy matching
  if (!rec) {
    rec = getFuzzyRecommendation(currentAnswers);
  }

  if (!rec) {
    rec = quizData.recommendations['yes-small_medium_basic_just-wordpress_moderate'];
  }

  showResults(rec);
}

function getFuzzyRecommendation(answers) {
  const scoreMap = {
    revenue: {
      'no': 1,
      'yes-small': 2,
      'yes-medium': 3,
      'yes-high': 4
    },
    traffic: {
      'low': 1,
      'medium': 2,
      'high': 3,
      'very-high': 4
    },
    technical: {
      'none': 1,
      'basic': 2,
      'intermediate': 3,
      'advanced': 4
    }
  };

  const score = (scoreMap.revenue[answers.revenue] || 2) +
                (scoreMap.traffic[answers.traffic] || 2) +
                (scoreMap.technical[answers.technical] || 2);

  if (score <= 4) {
    return quizData.recommendations['no_low_none_just-wordpress_minimal'];
  } else if (score <= 7) {
    return quizData.recommendations['yes-small_medium_basic_just-wordpress_moderate'];
  } else if (score <= 10) {
    return quizData.recommendations['yes-medium_high_basic_just-wordpress_moderate'];
  } else {
    return quizData.recommendations['yes-high_high_intermediate_wordpress-plus_comfortable'];
  }
}

function showResults(recommendation) {
  document.getElementById('progress-bar').style.display = 'none';
  document.getElementById('quiz-question-container').style.display = 'none';
  const resultsDiv = document.getElementById('quiz-results');
  resultsDiv.style.display = 'block';

  let html = `
    <div class="recommendation-card">
      <div class="recommendation-header">
        <h2>Your Hosting Recommendation</h2>
        <div class="recommendation-tier-badge">${recommendation.tier}</div>
      </div>

      <div class="recommendation-explanation">
        <strong>Why this tier for you:</strong> ${recommendation.explanation}
      </div>

      <h3 style="color: #333; font-size: 1.4em; margin-top: 40px; margin-bottom: 20px;">Top Providers</h3>
      ${recommendation.providers.map(p => `
        <div class="provider-suggestion">
          <h4>${p.name}</h4>
          <div class="provider-price">${p.price}</div>
          <div class="provider-reason">💡 ${p.reason}</div>
        </div>
      `).join('')}

      <div class="results-cta">
        <p><strong>Ready to learn more?</strong></p>
        <a href="/choose-hosting/">📚 Read Hosting Guide</a>
        <a href="/comparison/">⚖️ Compare Providers</a>
      </div>

      <div class="take-again-btn">
        <button class="btn btn-secondary" onclick="resetQuiz()">Take Quiz Again</button>
      </div>
    </div>
  `;

  document.getElementById('results-content').innerHTML = html;
}

function resetQuiz() {
  currentAnswers = {};
  currentQuestion = 0;
  document.getElementById('progress-bar').style.display = 'block';
  document.getElementById('quiz-question-container').style.display = 'block';
  document.getElementById('quiz-results').style.display = 'none';
  renderQuestion();
}

// Initialize on page load
document.addEventListener('DOMContentLoaded', renderQuestion);
</script>
</style>

<script>
const quizData = {
  questions: [
    {
      id: 'revenue',
      question: 'Does your site generate revenue?',
      options: [
        { value: 'no', label: 'No – it\'s a hobby or portfolio site' },
        { value: 'yes-small', label: 'Yes – but revenue is under $10k/year' },
        { value: 'yes-medium', label: 'Yes – revenue is $10k-$100k/year' },
        { value: 'yes-high', label: 'Yes – revenue is over $100k/year' }
      ]
    },
    {
      id: 'traffic',
      question: 'How much monthly traffic do you expect?',
      options: [
        { value: 'low', label: 'Under 1,000 visitors/month' },
        { value: 'medium', label: '1,000-10,000 visitors/month' },
        { value: 'high', label: '10,000-100,000 visitors/month' },
        { value: 'very-high', label: 'Over 100,000 visitors/month' }
      ]
    },
    {
      id: 'technical',
      question: 'What\'s your technical comfort level?',
      options: [
        { value: 'none', label: 'Zero – I\'m non-technical' },
        { value: 'basic', label: 'Basic – I can Google and troubleshoot' },
        { value: 'intermediate', label: 'Intermediate – I\'m comfortable with servers' },
        { value: 'advanced', label: 'Advanced – Linux/command line is familiar' }
      ]
    },
    {
      id: 'setup',
      question: 'Do you need anything beyond WordPress?',
      options: [
        { value: 'just-wordpress', label: 'Just WordPress' },
        { value: 'wordpress-plus', label: 'WordPress + custom code/plugins' },
        { value: 'multiple', label: 'Multiple sites or platforms' }
      ]
    },
    {
      id: 'budget',
      question: 'What\'s your monthly hosting budget?',
      options: [
        { value: 'minimal', label: 'Under $10/month' },
        { value: 'moderate', label: '$10-30/month' },
        { value: 'comfortable', label: '$30-100/month' },
        { value: 'premium', label: 'Over $100/month' }
      ]
    }
  ],

  recommendations: {
    'no_low_none_just-wordpress_minimal': {
      tier: 'Shared Hosting',
      explanation: 'For hobby sites with minimal traffic, shared hosting is fine. You don\'t need premium features.',
      providers: [
        {
          name: 'Bluehost',
          price: '$2.95-4.95/month',
          reason: 'WordPress.org official recommendation. Easy for beginners, reliable for hobby sites.'
        },
        {
          name: 'Hostinger',
          price: '$2.99-3.99/month',
          reason: 'Good uptime, decent support. Balance of price and reliability.'
        }
      ],
      cta: 'Read our shared hosting guide for more options'
    },

    'yes-small_medium_basic_just-wordpress_moderate': {
      tier: 'Managed WordPress Hosting',
      explanation: 'Your site generates revenue and needs reliability. Managed hosting prevents costly downtime and performs well.',
      providers: [
        {
          name: 'Hostinger WordPress',
          price: '$9.99-19.99/month',
          reason: 'Great value for small business sites. Good support, WordPress-optimized.'
        },
        {
          name: 'Bluehost Pro',
          price: '$19.95+/month',
          reason: 'WordPress.org official. Better performance than shared. Good for growing sites.'
        },
        {
          name: 'SiteGround',
          price: '$2.99-7.99/month (promo)',
          reason: 'Excellent support, fast servers, WordPress-specialized.'
        }
      ],
      cta: 'Compare managed hosting providers side-by-side'
    },

    'yes-medium_high_basic_just-wordpress_moderate': {
      tier: 'Premium Managed WordPress Hosting',
      explanation: 'With growing traffic and revenue, you need fast, reliable hosting with expert support.',
      providers: [
        {
          name: 'Kinsta',
          price: '$35-100+/month',
          reason: 'Industry-leading performance. Fast servers, exceptional support, staging environments.'
        },
        {
          name: 'WP Engine',
          price: '$20-115+/month',
          reason: 'Enterprise-grade uptime. Best support team. Perfect for mission-critical sites.'
        },
        {
          name: 'Pressable',
          price: '$25-100+/month',
          reason: 'Automattic-owned (trusted). Very fast, great for content creators.'
        }
      ],
      cta: 'Read the complete guide to premium managed hosting'
    },

    'yes-high_high_intermediate_wordpress-plus_comfortable': {
      tier: 'Cloud Hosting / VPS',
      explanation: 'You have technical skills and need flexibility beyond what managed hosting offers.',
      providers: [
        {
          name: 'DigitalOcean',
          price: '$4-6+/month',
          reason: 'Simplest VPS interface. Great documentation. Minimal support but excellent for developers.'
        },
        {
          name: 'Linode',
          price: '$5-10+/month',
          reason: 'Similar to DigitalOcean with slightly better support. Very reliable.'
        },
        {
          name: 'Kinsta Cloud',
          price: '$50+/month',
          reason: 'If you want managed cloud with full control. Premium pricing for expert support.'
        }
      ],
      cta: 'Learn more about cloud hosting and VPS options'
    },

    'yes-high_very-high_advanced_multiple_premium': {
      tier: 'Enterprise Cloud Infrastructure',
      explanation: 'At your scale, you need full control and custom infrastructure. Consider consulting an expert.',
      providers: [
        {
          name: 'AWS / Google Cloud / Azure',
          price: '$50-500+/month',
          reason: 'Enterprise-grade. Complex but infinitely scalable.'
        },
        {
          name: 'Dedicated Server',
          price: '$80-300+/month',
          reason: 'Entire physical server is yours. Maximum control.'
        }
      ],
      cta: 'Read our advanced hosting guide for enterprise options'
    }
  },

  getKey: function(answers) {
    const keys = [
      answers.revenue,
      answers.traffic,
      answers.technical,
      answers.setup,
      answers.budget
    ];
    return keys.join('_');
  }
};

let currentAnswers = {};

function renderQuiz() {
  const container = document.getElementById('quiz-questions');
  container.innerHTML = quizData.questions.map((q, idx) => `
    <div class="quiz-question">
      <h3>Question ${idx + 1} of ${quizData.questions.length}</h3>
      <h4>${q.question}</h4>
      <div class="quiz-options">
        ${q.options.map(opt => `
          <div class="quiz-option">
            <label>
              <input type="radio" name="${q.id}" value="${opt.value}" onchange="currentAnswers['${q.id}'] = '${opt.value}'">
              ${opt.label}
            </label>
          </div>
        `).join('')}
      </div>
    </div>
  `).join('');

  container.innerHTML += `
    <div class="quiz-button-group">
      <button class="btn btn-primary" onclick="submitQuiz()">Get My Recommendation</button>
      <button class="btn btn-secondary" onclick="resetQuiz()">Start Over</button>
    </div>
  `;
}

function submitQuiz() {
  // Check all questions answered
  if (quizData.questions.length !== Object.keys(currentAnswers).length) {
    alert('Please answer all questions before submitting.');
    return;
  }

  // Try exact match first
  let key = quizData.getKey(currentAnswers);
  let rec = quizData.recommendations[key];

  // If no exact match, use fuzzy matching
  if (!rec) {
    rec = getFuzzyRecommendation(currentAnswers);
  }

  if (!rec) {
    // Default recommendation
    rec = quizData.recommendations['yes-small_medium_basic_just-wordpress_moderate'];
  }

  showResults(rec);
}

function getFuzzyRecommendation(answers) {
  // Scoring system to find best match
  const scoreMap = {
    revenue: {
      'no': 1,
      'yes-small': 2,
      'yes-medium': 3,
      'yes-high': 4
    },
    traffic: {
      'low': 1,
      'medium': 2,
      'high': 3,
      'very-high': 4
    },
    technical: {
      'none': 1,
      'basic': 2,
      'intermediate': 3,
      'advanced': 4
    }
  };

  const score = (scoreMap.revenue[answers.revenue] || 2) +
                (scoreMap.traffic[answers.traffic] || 2) +
                (scoreMap.technical[answers.technical] || 2);

  if (score <= 4) {
    return quizData.recommendations['no_low_none_just-wordpress_minimal'];
  } else if (score <= 7) {
    return quizData.recommendations['yes-small_medium_basic_just-wordpress_moderate'];
  } else if (score <= 10) {
    return quizData.recommendations['yes-medium_high_basic_just-wordpress_moderate'];
  } else {
    return quizData.recommendations['yes-high_high_intermediate_wordpress-plus_comfortable'];
  }
}

function showResults(recommendation) {
  document.getElementById('quiz-questions').style.display = 'none';
  const resultsDiv = document.getElementById('quiz-results');
  resultsDiv.style.display = 'block';

  let html = `
    <h2>Your Hosting Recommendation</h2>
    
    <div class="recommendation-card">
      <h3>Recommended Tier</h3>
      <div class="recommendation-tier">${recommendation.tier}</div>
      
      <div class="recommendation-explanation">
        <strong>Why:</strong> ${recommendation.explanation}
      </div>

      <h3>Top Providers for You</h3>
      ${recommendation.providers.map(p => `
        <div class="provider-suggestion">
          <h4>${p.name}</h4>
          <div class="provider-price">${p.price}</div>
          <div class="provider-reason">${p.reason}</div>
        </div>
      `).join('')}

      <div class="results-cta">
        <p><strong>Next Step:</strong> Check out our detailed hosting guides to learn more and compare providers side-by-side.</p>
        <a href="/choose-hosting/">Read the Complete Hosting Guide</a>
        <a href="/hosting-comparison/">Compare Providers</a>
      </div>
    </div>

    <div style="text-align: center; margin-top: 30px;">
      <button class="btn btn-secondary" onclick="resetQuiz()">Take Quiz Again</button>
    </div>
  `;

  document.getElementById('results-content').innerHTML = html;
}

function resetQuiz() {
  currentAnswers = {};
  document.getElementById('quiz-results').style.display = 'none';
  document.getElementById('quiz-questions').style.display = 'block';
  renderQuiz();
}

// Initialize on page load
document.addEventListener('DOMContentLoaded', renderQuiz);
</script>
