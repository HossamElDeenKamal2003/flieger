<template>
    <div class="parent">
      <div class="title">
        <h1>Frequently Asked Questions <br /> (FAQ)</h1>
        <p>Our browser faq below, if you can't find the answer in Gready</p>
      </div>
      <div class="faq-section">
        <div
          v-for="(faq, index) in faqs"
          :key="index"
          :class="['faq-item', { active: activeIndex === index }]"
        >
          <div class="question" @click="toggleAnswer(index)">
            <h3>{{ faq.question }}</h3>
            <span>{{ activeIndex === index ? '\u25BC' : '\u25B6' }}</span>
          </div>
          <div
            v-show="activeIndex === index"
            class="answer"
          >
            <p style="font-size: 1.5rem;">{{ faq.answer }}</p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "fourthComponent",
    data() {
      return {
        faqs: [
          { question: "Why should I choose FEGO?", answer: "Because FEGO is an Egyptian app, which we are very proud of, our prices are very affordable for everyone." },
          { question: "Why is FEGO cheap?", answer: "FEGO is affordable because we believe everyone deserves quality transport at a fair price." },
          { question: "Why is FEGO's service so friendly?", answer: "FEGO's service is friendly because we focus on understanding our customers and treating them like family." },
          { question: "24/7 customer services?", answer: "We challenge ourselves to provide you with a response within 2 minutes, 24/7." },
          { question: "How to order FEGO?", answer: "With just two clicks, the car you ordered will be here. If you have any questions, don't hesitate to reach out, and you'll receive a response within 2 minutes, guaranteed." },
        ],
        activeIndex: null, // Tracks the currently active question
      };
    },
    methods: {
      toggleAnswer(index) {
        this.activeIndex = this.activeIndex === index ? null : index;
      },
    },
  };
  </script>
  
  <style scoped>
  .parent {
    max-width: 80%;
    margin: 0 auto;
    font-family: Arial, sans-serif;
  }
  
  .title h1 {
    text-align: center;
    font-size: 2rem;
    color: #333;
  }
  
  .title p {
    text-align: center;
    color: #666;
    margin-bottom: 20px;
  }
  
  .faq-section {
    padding: 10px;
    background-color: white;
  }
  
  .faq-item {
    margin-bottom: 15px;
    border: 1px solid #ddd;
    border-radius: 8px;
    overflow: hidden;
    transition: background-color 0.3s ease;
  }
  
  .faq-item.active {
    background: rgba(143, 0, 255, 1);
    color: #fff;
  }
  
  .question {
    display: flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;
    font-size: 1rem;
    padding: 30px;
    transition: background-color 0.3s ease, color 0.3s ease;
  }
  
  .question h3 {
    margin: 0;
  }
  
  .question span {
    font-size: 1.2rem;
  }
  
  .answer {
    padding: 15px;
    background-color: #fff;
    color: #333;
    animation: fadeIn 0.3s ease;
  }
  
  @keyframes fadeIn {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }
  </style>
  