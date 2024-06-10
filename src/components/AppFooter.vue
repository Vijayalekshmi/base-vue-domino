<template>
    <div class="container">
      <span>
        Developed by the
        <a href="https://data-directory.shared-services.domino-printing.org/data-platform-team/" target="_blank">Data Platform Team</a>
      </span>
      <span>Version {{ appVersion }}</span>
    </div>
  </template>
  
  <script setup>
  const appVersion = import.meta.env.VITE_APP_VERSION
  </script>
  
  <style scoped>
  .container {
    display: flex;
    flex-grow: 1;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
    padding: 1rem;
    background-color: var(--primary-color);
    row-gap: 0.25rem;
  }
  
  a {
    color: var(--primary-color-text);
  }
  
  a :hover {
    color: var(--highlight-text-color);
  }
  </style>
  