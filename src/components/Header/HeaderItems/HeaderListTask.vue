  <script setup>
  import { inject, ref } from 'vue'
  import Popup from '@/components/Header/HeaderItems/Popup.vue'

  const { cards } = inject('cards')

  defineProps({
    toggleButton: Boolean
  })

  let showPopupIndex = ref(null)

  const openPopup = (id) => {
    showPopupIndex.value = id
  }

  const closePopup = () => {
    showPopupIndex.value = null
  }
  </script>

  <template>
    <div class="changing-tasks-list__headers">
      <h4 class="changing-tasks-list__headers-title">Задачи</h4>
      <h4 class="changing-tasks-list__headers-title">Статус</h4>
    </div>
    <ul class="changing-tasks-list__ul">
      <li
        v-for="card in (toggleButton ? cards : cards.slice(0, 5))"
        :key="card.id"
        class="changing-tasks-list__ul-li"
      >
        <p class="changing-tasks-list__ul-li-text">{{ card.text }}</p>
        <div class="changing-tasks-list__ul-li-wrapper">
          <span class="changing-tasks-list__ul-li-status" @click="openPopup(card.id)">{{ card.status }}</span>
          <template v-if="showPopupIndex === card.id">
            <Teleport to="#app">
              <Popup :card="card" @closePopup="closePopup" />
            </Teleport>
          </template>
        </div>
      </li>
    </ul>
  </template>

  <style lang="scss" scoped>
  @import '@/common/varibles';
  @import '@/common/mixins';

  .changing-tasks-list__headers {
    display: flex;
    justify-content: space-between;
    width: 100%;
    margin: 0 0 24px 0;

    &-title {
      @include pt-sans-caption-text(18px);
      line-height: 26px;
      font-weight: 700;
      color: $color-text;
    }

    &-title:nth-child(2) {
      max-width: 102px;
      width: 100%;
      text-align: center;
    }
  }

  .changing-tasks-list__ul {
    &-li {
      display: flex;
      width: 100%;
      justify-content: space-between;
      border-bottom: 2px solid $color-border;
      align-items: center;
      margin: 0 0 10px 0;

      &:last-child {
        margin: 0;
        border-bottom: none;
      }

      &-text {
        @include pt-sans-caption-text(16px);
        line-height: 24px;
        font-weight: 400;
        color: $color-text;
      }

      .changing-tasks-list__ul-li-wrapper {
        max-width: 102px;
        width: 100%;
        text-align: center;
        display: flex;
        justify-content: center;
        position: relative;
      }

      &-status {
        @include pt-sans-caption-text(12px);
        font-weight: 400;
        line-height: 20px;
        box-sizing: border-box;
        padding: 5px 16px;
        background-color: $color-gray;
        color: $color-text;
        border-radius: 39px;
        margin: 0 0 5px;
      }
    }
  }

  @media screen and (max-width: $phone) {
    .changing-tasks-list__headers {
      &-title {
        @include montserrat-text(20px);
        line-height: 28px;
        color: $color-text;
      }

      &-title:nth-child(2) {
        display: none;
      }
    }

    .changing-tasks-list__ul {
      &-li {
        width: 100%;
        flex-direction: column;
        justify-content: center;
        align-items: start;
        background-color: $color-white;
        border-bottom: none;
        border-radius: 32px;
        padding: 24px;
        margin: 0 0 24px 0;

        &:last-child {
          margin: 0;
          border-bottom: none;
        }

        .changing-tasks-list__ul-li-wrapper{
          max-width: none;
        }

        &-text {
          font-weight: 700;
          line-height: 24px;
          margin: 0 0 20px;
        }

        div {
          max-width: none;
          width: 100%;
          text-align: center;
          display: flex;
          justify-content: center;
        }

        &-status {
          @include pt-sans-caption-text(14px);
          font-weight: 700;
          line-height: 24px;
          padding: 12px 32px;
          color: $color-orange;
          background-color: transparent;
          border: 2px solid $color-orange;
          border-radius: 50px;
          margin: 0;
          width: 100%;
        }
      }
    }
  }
  </style>
