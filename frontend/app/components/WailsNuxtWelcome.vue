<script setup lang="ts">
declare global {
  interface Window {
    runtime: {
      BrowserOpenURL: (url: string) => void;
    };
  }
}

const openUrl = (url: string) => {
  if (window.runtime?.BrowserOpenURL) {
    window.runtime.BrowserOpenURL(url);
  } else {
    window.open(url, "_blank");
  }
};
</script>

<template>
  <div class="container">
    <div class="gradient-overlay" />

    <div class="content-wrapper">
      <div class="content-box">
        <div class="header-section">
          <h1 class="title">
            Welcome to Wails +
            <span class="accent">Nuxt</span>
          </h1>

          <p class="description">
            You're all set! Start building your desktop application using Wails
            + Nuxt.
          </p>
        </div>
        <div class="button-group">
          <button @click="openUrl('https://wails.io/')" class="primary-button">
            Wails Docs
          </button>
          <button @click="openUrl('https://nuxt.com/')" class="primary-button">
            Nuxt Docs
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
}

.container {
  position: relative;
  min-height: 100vh;
  background-color: #030712;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, sans-serif;
}

.gradient-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, rgba(0, 220, 130, 0.05), transparent);
  pointer-events: none;
}

.content-wrapper {
  position: relative;
  padding: 1.5rem;
}

.content-box {
  max-width: 42rem;
  width: 100%;
}

.header-section {
  margin-bottom: 3rem;
}

.title {
  font-size: 3rem;
  font-weight: 700;
  color: #ffffff;
  margin-bottom: 1rem;
  line-height: 1.2;
}

.accent {
  color: #00dc82;
}

.description {
  font-size: 1.125rem;
  color: #d1d5db;
  line-height: 1.6;
}

.button-group {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.primary-button {
  border-radius: 0.375rem;
  font-weight: 500;
  display: inline-flex;
  align-items: center;
  transition: background-color 0.2s ease;
  padding: 0.5rem 1rem;
  font-size: 0.875rem;
  gap: 0.5rem;
  color: #111827;
  background-color: #00dc82;
  border: none;
  cursor: pointer;
}

.primary-button:hover {
  background-color: #00c972;
}
</style>
