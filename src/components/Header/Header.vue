<script setup>
import CurrentTask from '@/components/Header/HeaderItems/CurrentTask.vue'
import AddTask from '@/components/Header/HeaderItems/AddTask.vue'
import HeaderListTask from '@/components/Header/HeaderItems/HeaderListTask.vue'
import { inject, ref } from 'vue'

const { cards } = inject('cards')
const toggleButton = ref(false);

const scrollToTop = () => {
    const block = document.querySelector('.changing-tasks-list__position');
    block.scrollIntoView({ behavior: 'smooth' });
  }

</script>

<template>
  <div class="changing-tasks">
    <h1 class="changing-tasks__title">ToDo List Scloud</h1>
    <div class="changing-tasks__position">
      <CurrentTask />
      <AddTask />
    </div>
    <div class="changing-tasks-list__position">
      <HeaderListTask :toggleButton="toggleButton"/>
    </div>
    <button v-if="cards.length > 5"  class="changing-tasks-list__position-button" @click="toggleButton = !toggleButton; scrollToTop()">
      {{ toggleButton ? 'Скрыть' : 'Показать ещё' }}
    </button>
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

  .changing-tasks-list__position-button {
    @include pt-sans-caption-text(14px);
    font-weight: 700;
    line-height: 24px;
    color: $color-orange;
    border: 2px solid $color-orange;
    border-radius: 50px;
    padding: 12px 32px;
    background-color: $color-white;
    margin: 40px 0 0;
  }

  .changing-tasks-list__position-button:active{
    opacity: 0.5;
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

    .changing-tasks-list__position {
      background: transparent;
      padding: 0;
    }
  }
}
</style>
