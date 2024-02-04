<script setup>
import { inject, ref } from 'vue'

const { addToCards, id } = inject('cards')

const text = ref('')

const handleSubmit = () => {
  addToCards({
    id: id.value++,
    text: text.value,
    status: 'Открыт'
  })
  text.value = ''
}

const clearText = () => {
  text.value = ''
}


</script>

<template>
  <div class="changing-tasks__add">
    <h3 class="changing-tasks__add-title">Добавить задачу</h3>
    <form class="changing-tasks__add-form" @submit.prevent="handleSubmit">
      <button type="submit" class="changing-tasks__add-form-button">Добавить задачу</button>
      <div class="changing-tasks__add-form-wrapper">
        <input v-model="text" placeholder="Текст" class="changing-tasks__add-form-wrapper-input" />
        <button class="changing-tasks__add-form-wrapper-button" @click="clearText"></button>
      </div>
    </form>
  </div>
</template>

<style lang="scss" scoped>
@import '@/common/varibles';
@import '@/common/mixins';

.changing-tasks__add {
  border-radius: 48px;
  background-color: $color-white;
  padding: 40px 24px;
  max-width: 588px;
  width: 100%;

  &-title {
    @include pt-sans-caption-text(24px);
    font-weight: 700;
    line-height: 32px;
    color: $color-text;
    margin: 0 0 24px;
  }

  &-form {
    display: flex;
    justify-content: space-between;

    &-button {
      width: 44px;
      font-size: 0;
      height: 44px;
      background: $color-orange;
      border-radius: 50%;
      position: relative;
      border-color: transparent;

      &:after {
        position: absolute;
        content: '';
        background: $color-white;
        top: 20px;
        left: 12px;
        width: 17px;
        height: 2px;
        border-radius: 1px;
      }

      &:before {
        position: absolute;
        content: '';
        background: $color-white;
        top: 20px;
        left: 12px;
        width: 17px;
        height: 2px;
        border-radius: 1px;
        transform: rotate(90deg);
      }
    }

    &-wrapper {
      width: 90%;
      position: relative;

      &:hover .changing-tasks__add-form-wrapper-button {
        display: block;
      }

      &-input {
        @include pt-sans-caption-text(14px);
        line-height: 24px;
        font-weight: 400;
        width: 100%;
        border-radius: 100px;
        padding: 12px 0 12px 16px;
        border: 1px solid $color-border;

      }

      &-input:focus + .changing-tasks__add-form-wrapper-button {
        display: block;
      }

      &-button {
        position: absolute;
        width: 11px;
        height: 11px;
        top: 18px;
        right: 26px;
        cursor: pointer;
        display: none;
        background-color: transparent;
        border-color: transparent;
      }

      &-button:active {
        opacity: 0.5;
      }

      &-button:after {
        content: '';
        position: absolute;
        background-color: $color-orange;
        width: 2px;
        height: 14px;
        border-radius: 2px;
        right: 4px;
        top: -1px;
        transform: rotate(135deg);
      }

      &-button:before {
        content: '';
        position: absolute;
        background-color: $color-orange;
        width: 2px;
        height: 14px;
        border-radius: 3px;
        right: 4px;
        top: -1px;
        transform: rotate(45deg);
      }
    }
  }
}

@media screen and (max-width: 1190px) {
  .changing-tasks__add {
    max-width: none;

    &-form {

      &-input {
        @include pt-sans-caption-text(14px);
        max-width: none;
        margin: 0 0 0 40px;
      }
    }
  }
}

@media screen and (max-width: $tablet) {
  .changing-tasks__add {
    &-title {
      @include pt-sans-caption-text(18px);
      line-height: 26px;
      margin: 0 0 24px;
    }

    &-form {
      &-wrapper {
        &-button {
          display: block;
        }
      }
    }
  }
}


@media screen and (max-width: $phone) {
  .changing-tasks__add {
    padding: 24px;

    &-form {
      flex-direction: column-reverse;
      justify-content: center;

      &-button {
        @include pt-sans-caption-text(14px);
        font-weight: 700;
        line-height: 24px;
        padding: 8px 24px;
        color: $color-white;
        width: 100%;
        height: auto;
        background: $color-orange;
        border-radius: 50px;
        position: static;
        border-color: transparent;
      }

      &-wrapper {
        width: 100%;
        margin: 0 0 24px;

        &-input {
          @include pt-sans-caption-text(14px);
        }
      }
    }
  }
}

</style>