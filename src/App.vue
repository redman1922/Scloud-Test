<script setup lang="ts">
import Header from '@/components/Header/Header.vue'
import TaskBoard from '@/components/TaskBoard/TaskBoard.vue'
</script>

<template>
  <header class="wrapper-changing-tasks">
   <Header/>
  </header>
  <main class="wrapper-view-tasks">
    <TaskBoard/>
  </main>
  <footer class="footer"></footer>
</template>

<style lang="scss" scoped>
@import './common/varibles';
@import './common/mixins';

.wrapper-changing-tasks {
  background-color: $color-gray;
  padding: 64px 0;
}

.wrapper-view-tasks {
  width: 100%;
  max-width: 1200px;
  margin: 60px auto;
}

.footer{
  width: 100%;
  background: $color-dark-gray;
  height: 148px;
  border-radius: 48px 48px 0 0;
}
</style>
