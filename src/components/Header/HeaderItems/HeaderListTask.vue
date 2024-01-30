<template>
  <div class="changing-tasks-list__headers">
    <h4 class="changing-tasks-list__headers-title">Задачи</h4>
    <h4 class="changing-tasks-list__headers-title">Статус</h4>
  </div>
  <ul class="changing-tasks-list__ul">
    <li class="changing-tasks-list__ul-li">
      <p class="changing-tasks-list__ul-li-text">Сварить пельмени</p>
      <div>
        <span class="changing-tasks-list__ul-li-status">Открыт</span>
      </div>
    </li>
    <li class="changing-tasks-list__ul-li">
      <p class="changing-tasks-list__ul-li-text">Поднять инфрастуктуру проекта</p>
      <div>
        <span class="changing-tasks-list__ul-li-status">Открыт</span>
      </div>
    </li>
    <li class="changing-tasks-list__ul-li">
      <p class="changing-tasks-list__ul-li-text">
        Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу
      </p>
      <div>
        <span class="changing-tasks-list__ul-li-status">В работе</span>
      </div>
    </li>
    <li class="changing-tasks-list__ul-li">
      <p class="changing-tasks-list__ul-li-text">Поругаться с девопсом</p>
      <div>
        <span class="changing-tasks-list__ul-li-status">В работе</span>
      </div>
    </li>
    <li class="changing-tasks-list__ul-li">
      <p class="changing-tasks-list__ul-li-text">Спеть - Знаешь ли ты, вдоль ночных дорог</p>
      <div>
        <span class="changing-tasks-list__ul-li-status">Закрыт</span>
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
    }

    &-text {
      @include pt-sans-caption-text(16px);
      line-height: 24px;
      font-weight: 400;
      color: $color-text;
    }

    div {
      max-width: 102px;
      width: 100%;
      text-align: center;
      display: flex;
      justify-content: center;
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
</style>