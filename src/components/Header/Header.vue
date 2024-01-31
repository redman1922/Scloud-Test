<script setup lang="ts">
import CurrentTask from '@/components/Header/HeaderItems/CurrentTask.vue'
import AddTask from '@/components/Header/HeaderItems/AddTask.vue'
import HeaderListTask from '@/components/Header/HeaderItems/HeaderListTask.vue'
</script>

<template>
  <div class="changing-tasks">
    <h1 class="changing-tasks__title">ToDo List Scloud</h1>
    <div class="changing-tasks__position">
      <CurrentTask />
      <AddTask />
    </div>
    <div class="changing-tasks-list__position">
      <HeaderListTask />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import '@/common/varibles';
@import '@/common/mixins';

.changing-tasks {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;

  .changing-tasks__title {
    @include montserrat-text(32px);
    line-height: 40px;
    color: $color-text;
    margin: 0 0 48px 0;
  }

  .changing-tasks__position {
    width: 100%;
    display: flex;
    justify-content: space-between;
    margin: 0 0 60px 0;
  }

  .changing-tasks-list__position {
    background-color: $color-white;
    padding: 40px;
    max-width: 1200px;
    width: 100%;
    border-radius: 48px;
  }
}

@media screen and (max-width: 1190px) {
  .changing-tasks__position {
    flex-direction: column;
    justify-content: center;
  }
}

@media screen and (max-width: $tablet) {
  .changing-tasks {
    .changing-tasks__title {
      @include montserrat-text(24px);
      line-height: 32px;
      margin: 0 0 40px 0;
    }

    .changing-tasks-list__position {
      border-radius: 32px;
    }
  }
}

@media screen and (max-width: $phone) {
  .changing-tasks {
    .changing-tasks__title {
      @include montserrat-text(20px);
      line-height: 28px;
      margin: 0 0 32px 0;
    }

    .changing-tasks-list__position{
      background: transparent;
      padding: 0;
    }
  }
}
</style>
