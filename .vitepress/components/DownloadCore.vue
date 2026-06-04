<template>
  <div class="download-core">
    <!-- 加载中状态 -->
    <template v-if="!releaseData">
      <div class="loading-placeholder">⏳ 加载中...</div>
    </template>
    <template v-else>
      <!-- 错误状态 -->
      <div v-if="releaseData.error" class="error-placeholder">
        ⚠️ {{ releaseData.error }}
      </div>
      <!-- 正常状态 -->
      <template v-else>
        <!-- 根据 type 渲染不同触发器 -->
        <template v-if="type === 'link'">
          <a class="download-link" @click="download">
            📥 {{ buttonLabel }}
          </a>
        </template>

        <template v-else-if="type === 'card'">
          <div class="download-card" @click="download">
            <div class="card-content">
              <div class="card-icon">📦</div>
              <div class="card-text">
                <h3>{{ buttonLabel }}</h3>
                <!-- 版本号移到这里 -->
                <p v-if="showVersion && releaseData.tag_name" class="version-note">
                  {{ releaseData.tag_name }}
                </p>
              </div>
            </div>
          </div>
        </template>

        <template v-else>
          <button class="download-icon-btn" @click="download">
            <span class="icon">⬇️</span>
            <span>{{ buttonLabel }}</span>
          </button>
          <!-- 版本号显示在按钮下方 -->
          <div v-if="showVersion && releaseData.tag_name" class="version-below-button">
            {{ releaseData.tag_name }}
          </div>
        </template>
      </template>
    </template>
  </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  type: String,
  releaseData: {
    type: Object,
    default: null   // { tag_name, download_url, error }
  },
  bestMirrorUrl: String,
  osDisplayName: String,
  archDisplayName: String,
  label: String,          // "正式版" 或 "预发布版"
  showVersion: {
    type: Boolean,
    default: true
  }
});

const finalDownloadUrl = computed(() => {
  if (!props.releaseData?.download_url) return null;
  if (!props.bestMirrorUrl) return props.releaseData.download_url;
  return `${props.bestMirrorUrl}${props.releaseData.download_url}`;
});

// 按钮上固定文字，不再包含版本号
const buttonLabel = computed(() => `下载${props.label}`);

function download() {
  if (finalDownloadUrl.value) {
    window.open(finalDownloadUrl.value, '_blank');
  } else {
    alert('下载链接无效');
  }
}
</script>

<style scoped>
.download-core {
  display: inline-block;
}
.loading-placeholder, .error-placeholder {
  padding: 0.5rem 1rem;
  color: #666;
  font-size: 0.9rem;
}
.download-link {
  color: #3eaf7c;
  text-decoration: none;
  font-size: 1rem;
  cursor: pointer;
  border-bottom: 1px dashed #3eaf7c;
}
.download-link:hover {
  color: #2c8c5a;
  border-bottom-style: solid;
}
.download-icon-btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background: linear-gradient(135deg, #3eaf7c 0%, #2c8c5a 100%);
  border: none;
  color: white;
  padding: 12px 28px;
  border-radius: 50px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.2s, box-shadow 0.2s;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
.download-icon-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
}
.download-icon-btn .icon {
  font-size: 1.2rem;
}
/* 版本号显示在按钮下方（图标按钮样式） */
.version-below-button {
  margin-top: 6px;
  font-size: 0.8rem;
  color: #4e6e8e;
  text-align: center;
}
.download-card {
  display: inline-block;
  border: 1px solid #e2e8f0;
  border-radius: 16px;
  padding: 1rem 1.5rem;
  cursor: pointer;
  transition: box-shadow 0.2s, transform 0.1s;
  background: #fff;
  max-width: 280px;
  margin: 0 auto;
}
.download-card:hover {
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  transform: scale(1.02);
}
.card-content {
  display: flex;
  align-items: center;
  gap: 1rem;
}
.card-icon {
  font-size: 2rem;
}
.card-text {
  text-align: left;
}
.card-text h3 {
  margin: 0 0 0.25rem;
  font-size: 1.1rem;
}
/* 卡片内的版本号 */
.version-note {
  margin: 0;
  font-size: 0.8rem;
  color: #4e6e8e;
}
</style>