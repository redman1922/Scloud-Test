<script setup>
import { inject, ref } from 'vue'

const { updateCards, removeCards } = inject('cards')

const props = defineProps({
  card: {
    id: Number,
    text: String,
    status: String
  }
})
const emit = defineEmits(['closePopup']);

let textPopup = ref(props.card.text);
let statusPopup = ref(props.card.status);

const handleStatus = (status) => {
  switch (status) {
    case 'Открыт':
      statusPopup.value  = 'Открыт'
      break
    case 'В работе':
      statusPopup.value = 'В работе'
      break
    case 'Закрыт':
      statusPopup.value = 'Закрыт'
      break

  }
}

const handleForm = (id) =>{
  updateCards({
    id: id,
    text: textPopup.value,
    status: statusPopup
  })
  emit('closePopup')
}



</script>

<template>
  <div class="popup" @click="() => emit('closePopup')">
    <div class="popup-content" @click.stop="">
      <div class="popup-content__header">
        <h4 class="popup-content__header-title">Изменение задачи</h4>
        <button class="popup-content__header-button" @click="() => emit('closePopup')"></button>
      </div>
      <form class="popup-content__form" @submit.prevent="handleForm(card.id)">
        <input
          v-model="textPopup"
          class="popup-content__form-input"
          placeholder="Текст задачи, который можно изменить"
        />
        <div class="popup-content__form-list">
          <button
            v-if="card.status === 'Открыт'"
            :disabled="statusPopup === 'В работе'"
            class="popup-content__form-list-button"
            @click.prevent="handleStatus('В работе')"
          >В работу
          </button>
          <button
            v-if="card.status === 'Открыт' || card.status === 'В работе'"
            :disabled="statusPopup === 'Закрыт'"
            class="popup-content__form-list-button"
            @click.prevent="handleStatus('Закрыт')"
          >Закрыть
          </button>
          <button
            v-if="card.status === 'В работе'"
            :disabled="statusPopup === 'Открыт'"
            class="popup-content__form-list-button"
            @click.prevent="handleStatus('Открыт')"
          >Отложить
          </button>
          <button
            v-if="card.status === 'Закрыт'"
            :disabled="statusPopup === 'Открыт'"
            class="popup-content__form-list-button"
            @click.prevent="handleStatus('Открыт')"
          >Переоткрыть
          </button>

        </div>
        <div class="popup-content__footer">
          <button type="submit" class="popup-content__footer-accept">Применить</button>
          <button class="popup-content__footer-delete" @click="removeCards(card.id)">Удалить задачу</button>
        </div>
      </form>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import '@/common/varibles';
@import '@/common/mixins';

.popup {
  height: 100%;
  width: 100%;
  position: absolute;
  background-color: rgba(0, 0, 0, 0.5);
  top: 0;
  left: 0;
  z-index: 1;

  .popup-content {
    position: absolute;
    max-width: 375px;
    width: 100%;
    padding: 24px;
    background-color: $color-white;
    border-radius: 16px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 2;

    &__header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin: 0 0 24px;

      &-title {
        @include montserrat-text(18px);
        line-height: 26px;
        color: $color-text;
      }

      &-button {
        width: 14px;
        height: 14px;
        border: none;
        position: relative;
        background-color: transparent;
      }

      &-button:after {
        content: '';
        background-color: $color-dark-gray;
        width: 2px;
        height: 18px;
        top: -2px;
        left: 6px;
        border-radius: 5px;
        position: absolute;
        transform: rotate(45deg);
      }

      &-button:before {
        content: '';
        background-color: $color-dark-gray;
        width: 2px;
        height: 18px;
        top: -2px;
        left: 6px;
        border-radius: 5px;
        position: absolute;
        transform: rotate(135deg);
      }
    }

    &__form {

      &-input {
        @include pt-sans-caption-text(12px);
        line-height: 20px;
        color: $color-text;
        width: 100%;
        padding: 16px;
        border-radius: 20px;
        border: 1px solid $color-gray;
        margin: 0 0 16px;
      }

      &-list {
        border-top: 2px solid $color-gray;
        padding: 16px 0 24px;

        button {
          margin: 0 8px 0 0;
        }

        button:active {
          opacity: 0.5;
        }

        button:last-child {
          margin: 0;
        }

        &-button {
          @include pt-sans-caption-text(12px);
          line-height: 20px;
          font-weight: 400;
          padding: 5px 16px;
          background-color: $color-gray;
          color: $color-text;
          border-radius: 39px;
          border: none;
        }
        &-button:disabled {
          opacity: 0.5;
        }
      }
    }

    .popup-content__footer {
      display: flex;
      justify-content: space-between;

      &-accept {
        @include pt-sans-caption-text(14px);
        line-height: 24px;
        font-weight: 700;
        padding: 8px 24px;
        background-color: $color-orange;
        color: $color-white;
        border-radius: 50px;
        border: transparent;
      }

      &-delete {
        @include pt-sans-caption-text(14px);
        line-height: 24px;
        font-weight: 700;
        padding: 12px 32px;
        background-color: $color-white;
        color: $color-orange;
        border-radius: 50px;
        border: 2px solid $color-orange
      }
    }
  }
}
</style>