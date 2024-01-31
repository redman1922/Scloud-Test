<template>
  <h2 class="wrapper-view-tasks__title">Доска задач</h2>
  <div class="view-tasks__desk">
    <div class="view-tasks__desk-cards">
      <span class="view-tasks__desk-cards-status">Открыто</span>
      <ul class="view-tasks__desk-cards__list">
        <li>Сварить пельмени</li>
        <li>Поднять инфрастуктуру проекта</li>
      </ul>
    </div>
    <div class="view-tasks__desk-cards">
      <span class="view-tasks__desk-cards-status">В работе</span>
      <ul class="view-tasks__desk-cards__list">
        <li>Проснуться, улыбнуться, сделать отжимания, слетать на Марс и прочитать книгу</li>
        <li>Поругаться с девопсом</li>
      </ul>
    </div>
    <div class="view-tasks__desk-cards">
      <span class="view-tasks__desk-cards-status">Закрыто</span>
      <ul class="view-tasks__desk-cards__list">
        <li>Спеть - Знаешь ли ты, вдоль ночных дорог</li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import '@/common/varibles';
@import '@/common/mixins';

.wrapper-view-tasks__title {
  @include montserrat-text(32px);
  line-height: 40px;
  color: $color-text;
  margin: 0 0 48px;
}

.view-tasks__desk {
  display: flex;
  width: 100%;
  justify-content: space-between;

  &-cards {
    max-width: 389px;
    width: 100%;

    &-status {
      @include pt-sans-caption-text(20px);
      font-weight: 700;
      line-height: 28px;
      padding: 5px 24px;
      background-color: $color-gray;
      color: $color-text;
      border-radius: 39px;
    }
  }

  .view-tasks__desk-cards__list {
    list-style-type: none;
    max-width: 390px;
    width: 100%;
    background: $color-background-cards;
    padding: 16px;
    border-radius: 24px;
    min-height: 280px;
    margin: 24px 0 0;

    li{
      @include pt-sans-caption-text(16px);
      font-weight: 700;
      line-height: 24px;
      padding: 24px 32px;
      color: $color-text;
      background-color: $color-white;
      border-radius: 24px;
      margin: 0 0 16px;
      border: 2px solid $color-border;
    }

    li:last-child{
      margin: 0;
    }
  }
}


@media screen and (max-width: 1190px) {
  .view-tasks__desk {
    flex-wrap: wrap;
    justify-content: space-around;

    &-cards {
      text-align: center;
    }

    &-cards:last-child{
      margin: 50px 0 0;
    }
  }
}

</style>
