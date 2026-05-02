<template>
  <section id="contact" class="contact">
    <h2 class="section-title">联系我</h2>
    <p class="section-subtitle">有项目合作、技术交流或编程学习？欢迎随时联系我</p>
    <div class="contact-content">
      <div class="contact-methods">
        <a
          href="https://Jasonakeke.blog.csdn.net"
          target="_blank"
          rel="noopener noreferrer"
          class="contact-card"
        >
          <span class="contact-icon">📝</span>
          <div class="contact-info">
            <h3 class="contact-title">CSDN博客</h3>
            <p class="contact-value">Jasonakeke (8K粉)</p>
          </div>
        </a>

        <div class="contact-card qrcode-card">
          <span class="contact-icon">💬</span>
          <div class="contact-info">
            <h3 class="contact-title">公众号</h3>
            <p class="contact-value">柯柯的AI宝藏库</p>
            <div class="qrcode-container">
              <img 
                :src="gzhQrCode" 
                alt="公众号" 
                class="qrcode-image"
                @error="handleImageError('gzh', $event)"
                loading="lazy"
              />
              <div v-if="imageErrors.gzh" class="qrcode-fallback">
                <span class="fallback-icon">📱</span>
                <span class="fallback-text">公众号</span>
              </div>
            </div>
          </div>
        </div>

        <div class="contact-card qrcode-card">
          <span class="contact-icon">📱</span>
          <div class="contact-info">
            <h3 class="contact-title">微信</h3>
            <p class="contact-value">扫码添加</p>
            <div class="qrcode-container">
              <img 
                :src="wechatQrCode" 
                alt="微信" 
                class="qrcode-image"
                @error="handleImageError('wechat', $event)"
                loading="lazy"
              />
              <div v-if="imageErrors.wechat" class="qrcode-fallback">
                <span class="fallback-icon">💬</span>
                <span class="fallback-text">微信</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="contact-form-wrapper">
        <form class="contact-form" @submit.prevent="handleSubmit">
          <h3>发送消息</h3>
          <div v-if="submitStatus" :class="['status-message', submitStatus.type]">
            {{ submitStatus.message }}
          </div>
          <div class="form-group">
            <label for="name">姓名</label>
            <input type="text" id="name" v-model="formData.name" required placeholder="请输入您的姓名" :disabled="isSubmitting" />
          </div>
          <div class="form-group">
            <label for="email">邮箱</label>
            <input type="email" id="email" v-model="formData.email" required placeholder="请输入您的邮箱" :disabled="isSubmitting" />
          </div>
          <div class="form-group">
            <label for="message">消息</label>
            <textarea
              id="message"
              v-model="formData.message"
              rows="5"
              required
              placeholder="请输入您想说的话..."
              :disabled="isSubmitting"
            ></textarea>
          </div>
          <button type="submit" class="submit-btn" :disabled="isSubmitting">
            {{ isSubmitting ? '发送中...' : '发送消息' }}
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue'
import wechatQrCode from '../assets/images/wechat.jpg'
import gzhQrCode from '../assets/images/gzh.jpg'

const formData = reactive({
  name: '',
  email: '',
  message: ''
})

const isSubmitting = ref(false)
const submitStatus = ref(null)
const imageErrors = reactive({
  gzh: false,
  wechat: false
})

const handleImageError = (imageType, event) => {
  console.error(`图片加载失败: ${imageType}`, event)
  imageErrors[imageType] = true
}

const handleSubmit = async () => {
  isSubmitting.value = true
  submitStatus.value = null

  try {
    const response = await fetch('https://formsubmit.co/ajax/2284037977@qq.com', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'Accept': 'application/json'
      },
      body: JSON.stringify({
        name: formData.name,
        email: formData.email,
        message: formData.message,
        _subject: '来自个人网站的新消息',
        _captcha: 'false',
        _template: 'table'
      })
    })

    if (response.ok) {
      submitStatus.value = {
        type: 'success',
        message: '✓ 消息发送成功！我会尽快回复您。'
      }
      formData.name = ''
      formData.email = ''
      formData.message = ''

      setTimeout(() => {
        submitStatus.value = null
      }, 5000)
    } else {
      throw new Error('发送失败')
    }
  } catch (error) {
    submitStatus.value = {
      type: 'error',
      message: '✗ 发送失败，请稍后重试或直接添加微信联系'
    }
  } finally {
    isSubmitting.value = false
  }
}
</script>

<style scoped>
.contact {
  background-color: var(--bg-dark);
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  color: var(--text-dark);
  text-align: center;
  text-shadow: var(--glow-text);
  letter-spacing: 2px;
}

.section-subtitle {
  font-size: 1.1rem;
  color: var(--text-light);
  text-align: center;
  margin-bottom: 3rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.contact-content {
  max-width: 1000px;
  margin: 3rem auto 0;
}

.contact-methods {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
  margin-bottom: 3rem;
}

.contact-card {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1.5rem;
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  border-radius: 12px;
  border: 1px solid rgba(99, 102, 241, 0.1);
  transition: all 0.3s ease;
  text-decoration: none;
}

.contact-card:not(.qrcode-card):hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow);
  background: linear-gradient(135deg, rgba(99, 102, 241, 0.2), rgba(236, 72, 153, 0.2));
  border-color: var(--primary-color);
}

.contact-card:not(.qrcode-card):hover .contact-title,
.contact-card:not(.qrcode-card):hover .contact-value {
  color: white;
}

.qrcode-card {
  flex-direction: column;
  text-align: center;
  cursor: default;
}

.qrcode-container {
  position: relative;
  width: 150px;
  height: 150px;
  margin-top: 1rem;
  border-radius: 8px;
}

.qrcode-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 8px;
  border: 2px solid var(--primary-color);
  box-shadow: 0 0 20px rgba(99, 102, 241, 0.3);
  transition: all 0.3s ease;
}

.qrcode-image:hover {
  transform: scale(1.05);
  box-shadow: 0 0 30px rgba(99, 102, 241, 0.5);
}

.qrcode-fallback {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, rgba(99, 102, 241, 0.2), rgba(236, 72, 153, 0.2));
  border-radius: 8px;
  border: 2px solid var(--primary-color);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 0.5rem;
}

.fallback-icon {
  font-size: 2rem;
}

.fallback-text {
  font-size: 0.9rem;
  color: var(--text-dark);
  font-weight: 600;
}

.contact-icon {
  font-size: 2rem;
  flex-shrink: 0;
  filter: drop-shadow(0 0 5px var(--primary-color));
}

.contact-info {
  flex: 1;
}

.contact-title {
  font-size: 0.9rem;
  color: var(--primary-color);
  margin-bottom: 0.25rem;
  font-weight: 600;
  text-shadow: var(--glow-text);
}

.contact-value {
  font-size: 1rem;
  color: var(--text-dark);
  font-weight: 600;
}

.contact-form-wrapper {
  max-width: 600px;
  margin: 0 auto;
}

.contact-form {
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  padding: 2rem;
  border-radius: 16px;
  border: 1px solid rgba(99, 102, 241, 0.1);
}

.contact-form h3 {
  font-size: 1.5rem;
  margin-bottom: 1.5rem;
  color: var(--text-dark);
  text-align: center;
  text-shadow: var(--glow-text);
}

.status-message {
  padding: 1rem;
  border-radius: 8px;
  margin-bottom: 1.5rem;
  text-align: center;
  font-weight: 500;
  animation: slideIn 0.3s ease;
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.status-message.success {
  background: rgba(16, 185, 129, 0.1);
  border: 1px solid rgba(16, 185, 129, 0.3);
  color: var(--accent-color);
  box-shadow: 0 0 15px rgba(16, 185, 129, 0.2);
}

.status-message.error {
  background: rgba(239, 68, 68, 0.1);
  border: 1px solid rgba(239, 68, 68, 0.3);
  color: #ef4444;
  box-shadow: 0 0 15px rgba(239, 68, 68, 0.2);
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 500;
  color: var(--text-dark);
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 0.75rem 1rem;
  border: 2px solid rgba(99, 102, 241, 0.2);
  border-radius: 8px;
  font-size: 1rem;
  font-family: inherit;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
  background: rgba(10, 14, 39, 0.8);
  color: var(--text-dark);
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--primary-color);
  box-shadow: 0 0 15px rgba(99, 102, 241, 0.3);
}

.form-group textarea {
  resize: vertical;
}

.submit-btn {
  width: 100%;
  padding: 0.875rem;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  color: var(--bg-darker);
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 0 20px rgba(99, 102, 241, 0.3);
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 0 30px rgba(99, 102, 241, 0.5);
}

.submit-btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
  transform: none;
}

.form-group input:disabled,
.form-group textarea:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

@media (max-width: 768px) {
  .contact-methods {
    grid-template-columns: 1fr;
  }

  .contact-form {
    padding: 1.5rem;
  }
}
</style>
