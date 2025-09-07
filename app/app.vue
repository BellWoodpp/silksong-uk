<template>
  <div class="silksong-container">
    <header class="game-header">
      <div class="header-content">
        <h1 class="game-title">Hollow Knight: Silksong</h1>
        <div class="subtitle">The Hornet's Journey</div>
      </div>
    </header>
    
    <main class="game-main">
      <div class="content-wrapper">
        <section class="hero-section">
          <h2 class="section-title">Silksong</h2>
          <div class="game-description">
            <p class="description-text">
              Hollow Knight: Silksong is a 2D platformer game developed by Team Cherry. 
              It is the sequel to the 2017 game Hollow Knight, featuring Hornet as the protagonist.
            </p>
            <p class="description-text">
              Embark on an epic adventure through the kingdom of Pharloom, 
              where danger lurks in every shadow and mystery awaits around every corner.
            </p>
            <p class="description-text">
              Experience the critically acclaimed gameplay, immersive story, 
              and stunning hand-drawn art style that made the original a masterpiece.
            </p>
          </div>
        </section>
        
        <section class="features-section">
          <div class="feature-card" @click="showUnderConstruction('Exploration')">
            <h3>Exploration</h3>
            <p>Discover vast interconnected worlds filled with secrets and treasures.</p>
          </div>
          <div class="feature-card" @click="showUnderConstruction('Combat')">
            <h3>Combat</h3>
            <p>Master Hornet's agile fighting style with silk-based abilities.</p>
          </div>
          <div class="feature-card" @click="showUnderConstruction('Story')">
            <h3>Story</h3>
            <p>Unravel the mysteries of Pharloom and Hornet's destiny.</p>
          </div>
        </section>
      </div>
    </main>
    
    <!-- 施工中提示模态框 -->
    <div v-if="showModal" class="modal-overlay" @click="closeModal">
      <div class="modal-content" @click.stop>
        <div class="modal-header">
          <h3 class="modal-title">{{ selectedFeature }}</h3>
          <button class="close-btn" @click="closeModal">&times;</button>
        </div>
        <div class="modal-body">
          <div class="construction-icon">🚧</div>
          <p class="construction-text">Under Construction...</p>
          <p class="construction-subtext">Stay tuned for more exciting content!</p>
        </div>
      </div>
    </div>
    
    <footer class="game-footer">
      <div class="footer-content">
        <p>&copy; 2025 Team Cherry. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// 响应式数据
const showModal = ref(false)
const selectedFeature = ref('')

// 显示施工中提示
const showUnderConstruction = (feature) => {
  selectedFeature.value = feature
  showModal.value = true
}

// 关闭模态框
const closeModal = () => {
  showModal.value = false
  selectedFeature.value = ''
}
</script>

<style>
/* 导入Google字体 */
@import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700&family=Crimson+Text:ital,wght@0,400;0,600;1,400&display=swap');

/* 重置和基础样式 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  height: 100%;
  overflow-x: hidden;
}

/* 空洞骑士主题色彩 */
:root {
  --primary-dark: #0a0a0a;
  --secondary-dark: #1a1a1a;
  --accent-blue: #2c3e50;
  --accent-purple: #8e44ad;
  --accent-gold: #f39c12;
  --accent-silver: #bdc3c7;
  --text-primary: #ecf0f1;
  --text-secondary: #bdc3c7;
  --text-accent: #f39c12;
  --border-color: #34495e;
  --shadow-color: rgba(0, 0, 0, 0.8);
}

/* 主容器 */
.silksong-container {
  min-height: 100vh;
  background: linear-gradient(135deg, var(--primary-dark) 0%, var(--secondary-dark) 50%, var(--accent-blue) 100%);
  color: var(--text-primary);
  font-family: 'Crimson Text', serif;
  position: relative;
  overflow-x: hidden;
}

/* 背景装饰效果 */
.silksong-container::before {
  content: '';
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: 
    radial-gradient(circle at 20% 80%, rgba(142, 68, 173, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 80% 20%, rgba(243, 156, 18, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 40% 40%, rgba(44, 62, 80, 0.1) 0%, transparent 50%);
  pointer-events: none;
  z-index: 0;
}

/* 头部样式 */
.game-header {
  position: relative;
  z-index: 10;
  padding: 2rem 0;
  text-align: center;
  border-bottom: 2px solid var(--border-color);
  background: linear-gradient(90deg, transparent 0%, rgba(142, 68, 173, 0.1) 50%, transparent 100%);
}

.header-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.game-title {
  font-family: 'Cinzel', serif;
  font-size: 3.5rem;
  font-weight: 700;
  color: var(--text-accent);
  text-shadow: 
    0 0 10px rgba(243, 156, 18, 0.5),
    0 0 20px rgba(243, 156, 18, 0.3),
    0 0 30px rgba(243, 156, 18, 0.1);
  margin-bottom: 0.5rem;
  letter-spacing: 2px;
  animation: titleGlow 3s ease-in-out infinite alternate;
}

.subtitle {
  font-size: 1.2rem;
  color: var(--text-secondary);
  font-style: italic;
  letter-spacing: 1px;
}

/* 主内容区域 */
.game-main {
  position: relative;
  z-index: 10;
  padding: 3rem 0;
  min-height: calc(100vh - 200px);
}

.content-wrapper {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

/* 英雄区域 */
.hero-section {
  text-align: center;
  margin-bottom: 4rem;
}

.section-title {
  font-family: 'Cinzel', serif;
  font-size: 2.5rem;
  color: var(--accent-purple);
  margin-bottom: 2rem;
  text-shadow: 0 0 15px rgba(142, 68, 173, 0.5);
}

.game-description {
  max-width: 800px;
  margin: 0 auto;
}

.description-text {
  font-size: 1.1rem;
  line-height: 1.8;
  margin-bottom: 1.5rem;
  color: var(--text-primary);
  text-align: justify;
}

/* 特性卡片区域 */
.features-section {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 3rem;
}

.feature-card {
  background: linear-gradient(145deg, rgba(26, 26, 26, 0.8), rgba(44, 62, 80, 0.3));
  border: 1px solid var(--border-color);
  border-radius: 10px;
  padding: 2rem;
  text-align: center;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 32px var(--shadow-color);
  cursor: pointer;
  user-select: none;
}

.feature-card:hover {
  transform: translateY(-5px);
  border-color: var(--accent-gold);
  box-shadow: 
    0 12px 40px var(--shadow-color),
    0 0 20px rgba(243, 156, 18, 0.2);
}

.feature-card:active {
  transform: translateY(-2px);
  transition: all 0.1s ease;
}

.feature-card h3 {
  font-family: 'Cinzel', serif;
  font-size: 1.5rem;
  color: var(--accent-gold);
  margin-bottom: 1rem;
  text-shadow: 0 0 10px rgba(243, 156, 18, 0.3);
}

.feature-card p {
  color: var(--text-secondary);
  line-height: 1.6;
}

/* 页脚 */
.game-footer {
  position: relative;
  z-index: 10;
  padding: 2rem 0;
  text-align: center;
  border-top: 1px solid var(--border-color);
  background: linear-gradient(90deg, transparent 0%, rgba(44, 62, 80, 0.2) 50%, transparent 100%);
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.footer-content p {
  color: var(--text-secondary);
  font-size: 0.9rem;
}

/* 模态框样式 */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  backdrop-filter: blur(5px);
  animation: fadeIn 0.3s ease;
}

.modal-content {
  background: linear-gradient(145deg, rgba(26, 26, 26, 0.95), rgba(44, 62, 80, 0.8));
  border: 2px solid var(--accent-gold);
  border-radius: 15px;
  padding: 0;
  max-width: 400px;
  width: 90%;
  box-shadow: 
    0 20px 60px var(--shadow-color),
    0 0 30px rgba(243, 156, 18, 0.3);
  animation: slideIn 0.3s ease;
  backdrop-filter: blur(10px);
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 2rem;
  border-bottom: 1px solid var(--border-color);
  background: linear-gradient(90deg, rgba(142, 68, 173, 0.2), rgba(243, 156, 18, 0.1));
}

.modal-title {
  font-family: 'Cinzel', serif;
  font-size: 1.5rem;
  color: var(--accent-gold);
  margin: 0;
  text-shadow: 0 0 10px rgba(243, 156, 18, 0.3);
}

.close-btn {
  background: none;
  border: none;
  color: var(--text-secondary);
  font-size: 2rem;
  cursor: pointer;
  padding: 0;
  width: 30px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  transition: all 0.3s ease;
}

.close-btn:hover {
  color: var(--accent-gold);
  background: rgba(243, 156, 18, 0.1);
  transform: scale(1.1);
}

.modal-body {
  padding: 2rem;
  text-align: center;
}

.construction-icon {
  font-size: 4rem;
  margin-bottom: 1rem;
  animation: bounce 2s infinite;
}

.construction-text {
  font-size: 1.3rem;
  color: var(--text-primary);
  margin-bottom: 0.5rem;
  font-weight: 600;
}

.construction-subtext {
  color: var(--text-secondary);
  font-size: 1rem;
  font-style: italic;
}

/* 动画效果 */
@keyframes titleGlow {
  0% {
    text-shadow: 
      0 0 10px rgba(243, 156, 18, 0.5),
      0 0 20px rgba(243, 156, 18, 0.3),
      0 0 30px rgba(243, 156, 18, 0.1);
  }
  100% {
    text-shadow: 
      0 0 15px rgba(243, 156, 18, 0.7),
      0 0 25px rgba(243, 156, 18, 0.5),
      0 0 35px rgba(243, 156, 18, 0.3);
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(-50px) scale(0.9);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-10px);
  }
  60% {
    transform: translateY(-5px);
  }
}

/* 响应式设计 */
@media (max-width: 768px) {
  .game-title {
    font-size: 2.5rem;
  }
  
  .section-title {
    font-size: 2rem;
  }
  
  .features-section {
    grid-template-columns: 1fr;
  }
  
  .content-wrapper {
    padding: 0 1rem;
  }
  
  .header-content {
    padding: 0 1rem;
  }
  
  .modal-content {
    width: 95%;
    max-width: 350px;
  }
  
  .modal-header {
    padding: 1rem 1.5rem;
  }
  
  .modal-body {
    padding: 1.5rem;
  }
  
  .construction-icon {
    font-size: 3rem;
  }
  
  .construction-text {
    font-size: 1.1rem;
  }
}

@media (max-width: 480px) {
  .game-title {
    font-size: 2rem;
  }
  
  .section-title {
    font-size: 1.5rem;
  }
  
  .description-text {
    font-size: 1rem;
  }
  
  .modal-content {
    width: 95%;
    max-width: 300px;
  }
  
  .modal-header {
    padding: 1rem;
  }
  
  .modal-body {
    padding: 1rem;
  }
  
  .modal-title {
    font-size: 1.2rem;
  }
  
  .construction-icon {
    font-size: 2.5rem;
  }
  
  .construction-text {
    font-size: 1rem;
  }
  
  .construction-subtext {
    font-size: 0.9rem;
  }
}
</style>
