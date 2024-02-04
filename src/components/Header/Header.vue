<script setup>
import CurrentTask from '@/components/Header/HeaderItems/CurrentTask.vue'
import AddTask from '@/components/Header/HeaderItems/AddTask.vue'
import HeaderListTask from '@/components/Header/HeaderItems/HeaderListTask.vue'
import { inject, ref } from 'vue'

const { cards } = inject('cards')
const toggleButton = ref(false)

const scrollToTop = () => {
  const block = document.querySelector('.changing-tasks-list__position')
  block.scrollIntoView({ behavior: 'smooth' })
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
      <HeaderListTask
        :toggle-button="toggleButton"
      />
    </div>
    <button
      v-if="cards.length > 5"
      class="changing-tasks-list__position-button"
      @click="toggleButton = !toggleButton; scrollToTop()">
      {{ toggleButton ? 'Скрыть' : 'Показать ещё' }}
      <span :class="toggleButton ? 'arrow-up' : 'arrow-down'"></span>
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

  &__title {
    @include montserrat-text(32px);
    line-height: 40px;
    color: $color-text;
    margin: 0 0 48px 0;
  }

  &__position {
    width: 100%;
    display: flex;
    justify-content: space-between;
    margin: 0 0 60px 0;
  }

  &-list__position {
    background-color: $color-white;
    padding: 40px;
    max-width: 1200px;
    width: 100%;
    border-radius: 48px;

    &-button {
      @include pt-sans-caption-text(14px);
      font-weight: 700;
      line-height: 24px;
      color: $color-orange;
      border: 2px solid $color-orange;
      border-radius: 50px;
      padding: 12px 64px 12px 32px;
      background-color: $color-white;
      margin: 40px 0 0;
      position: relative;
    }

    &-button:active {
      opacity: 0.5;
    }
  }

  .arrow-up {
    position: absolute;
    width: 2px;
    height: 10px;
    background-color: #ff6600;
    border-radius: 1px;
    top: 19px;
    right: 35px;
    transform: rotate(135deg);
  }
  .arrow-up:after {
    content: "";
    position: absolute;
    width: 2px;
    height: 10px;
    background-color: #ff6600;
    border-radius: 1px;
    top: 4px;
    right: -4px;
    transform: rotate(90deg);
  }

  .arrow-down{
    position: absolute;
    width: 2px;
    height: 10px;
    background-color: #ff6600;
    border-radius: 1px;
    top: 19px;
    right: 41px;
    transform: rotate(135deg);
  }
  .arrow-down:after{
    content: "";
    position: absolute;
    width: 2px;
    height: 10px;
    background-color: #ff6600;
    border-radius: 1px;
    top: -4px;
    left: -5px;
    transform: rotate(90deg);
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
    &__title {
      @include montserrat-text(24px);
      line-height: 32px;
      margin: 0 0 40px 0;
    }

    &__position {
      border-radius: 32px;
    }
  }
}

@media screen and (max-width: $phone) {
  .changing-tasks {
    &__title {
      @include montserrat-text(20px);
      line-height: 28px;
      margin: 0 0 32px 0;
    }

    &-list__position {
      background: transparent;
      padding: 0;
    }
  }
}
</style>
