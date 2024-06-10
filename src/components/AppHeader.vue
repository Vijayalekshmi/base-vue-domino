<template>
    <div class="container">
      <div class="wrapper">
        <IconDeviceLogService class="logo"></IconDeviceLogService>
        <h1>Device Log Service- header changed</h1>
      </div>
      <!-- <form @submit.prevent="searchLocations" class="wrapper search">
          <InputText v-model="searchTerm" placeholder="search" class="input"></InputText>
          <Button rounded @click="searchLocations"
            ><template #icon> <i-mdi-search></i-mdi-search></template
          ></Button>
        </form> -->
  
      <div class="wrapper utils">
        <ThemeButton></ThemeButton>
        <Avatar shape="circle"><i-mdi-user /></Avatar>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import IconDeviceLogService from "./icons/IconDeviceLogService.vue"
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
  
  .wrapper {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    gap: 10px;
  }
  
  .search {
    order: 3;
  }
  
  .utils {
    justify-content: right;
    order: 2;
  }
  
  h1 {
    font-size: 1.5rem;
    font-weight: bold;
    color: var(--primary-color-text);
  }
  
  .logo {
    color: var(--primary-color-text);
  }
  
  @media (min-width: 768px) {
    h1 {
      font-size: 2rem;
    }
  
    .search {
      order: 1;
    }
  }
  </style>
  