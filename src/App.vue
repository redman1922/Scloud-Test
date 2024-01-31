<script setup lang="ts">
import Header from '@/components/Header/Header.vue'
import TaskBoard from '@/components/TaskBoard/TaskBoard.vue'
</script>

<template>
  <header class="wrapper-changing-tasks">
    <Header />
  </header>
  <main class="wrapper-view-tasks">
    <TaskBoard />
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
  margin: 60px auto 0;
  padding-bottom: 208px;
}

.footer {
  background: $color-dark-gray;
  height: 148px;
  border-radius: 48px 48px 0 0;
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
}

@media screen and (max-width: 1190px) {
  .wrapper-changing-tasks {
    padding: 64px 1%;
  }

  .wrapper-view-tasks {
    padding: 0 1% 208px;
  }
}

@media screen and (max-width: $tablet) {
  .wrapper-changing-tasks {
    padding: 48px 4% 180px;
  }

  .wrapper-view-tasks {
    display: none;
  }
  .footer {
    height: 120px;
  }
}

@media screen and (max-width: $phone) {
  .wrapper-changing-tasks {
    padding: 32px 4% 140px;
  }
  .footer {
    height: 80px;
  }
}
</style>
