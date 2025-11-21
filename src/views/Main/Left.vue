<template>
  <div :class="store.mobileOpenState ? 'left hidden' : 'left'">
    <Message />
    <SocialLinks />

    <!-- Google AdSense Block -->
    <ins
      class="adsbygoogle"
      style="display:block"
      data-ad-client="ca-pub-2160969409923714"
      data-ad-slot="6293176689"
      data-ad-format="auto"
      data-full-width-responsive="true"
    ></ins>
  </div>
</template>

<script setup>
import { onMounted } from "vue";
import { mainStore } from "@/store";
import Message from "@/components/Message.vue";
import SocialLinks from "@/components/SocialLinks.vue";

const store = mainStore();

// 加载 Google Ads 脚本
onMounted(() => {
  // 避免重复加载 script
  if (!document.querySelector('script[src^="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"]')) {
    const script = document.createElement("script");
    script.async = true;
    script.src =
      "https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-2160969409923714";
    script.crossOrigin = "anonymous";
    document.head.appendChild(script);
  }

  // 触发广告渲染
  (window.adsbygoogle = window.adsbygoogle || []).push({});
});
</script>

<style lang="scss" scoped>
.left {
  width: 50%;
  margin-right: 10px;
  transform: translateY(20px);

  &.hidden {
    display: none;
  }

  @media (max-width: 720px) {
    margin-right: 0;
    width: 100%;
  }
}
</style>
