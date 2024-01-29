<script setup lang="ts"></script>

<template>
  <div class="wrapper-changing-tasks">
    <div class="changing-tasks">
      <h1 class="changing-tasks__title">ToDo List Scloud</h1>
      <div class="changing-tasks__position">
        <div class="changing-tasks__current">
          <h3 class="changing-tasks__current-title">Текущие задачи</h3>
          <ul class="changing-tasks__current-ul">
            <li class="changing-tasks__current-li">
              <span class="changing-tasks__current-li-icon-1"><strong>Открыто - 2</strong></span>
            </li>
            <li class="changing-tasks__current-li">
              <span class="changing-tasks__current-li-icon-2"><strong>В работе - 2</strong></span>
            </li>
            <li class="changing-tasks__current-li">
              <span class="changing-tasks__current-li-icon-3"> <strong>Закрыто - 1</strong></span>
            </li>
          </ul>
        </div>
        <div class="changing-tasks__add">
          <h3 class="changing-tasks__add-title">Добавить задачу</h3>
          <form class="changing-tasks__add-form">
            <button class="changing-tasks__add-form-button" />
            <input placeholder="Текст" class="changing-tasks__add-form-input" />
          </form>
        </div>
      </div>
      <div class="changing-tasks-list__position">
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
      </div>
    </div>
  </div>
  <div class="wrapper-view-tasks">
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
  </div>
  <footer class="footer"></footer>
</template>

<style lang="scss" scoped>
@import './common/varibles';
@import './common/mixins';

.wrapper-changing-tasks {
  background-color: $color-gray;
  padding: 64px 0;

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

      .changing-tasks__current {
        border-radius: 48px;
        background-color: $color-white;
        padding: 40px 24px;
        max-width: 588px;
        width: 100%;

        .changing-tasks__current-title {
          @include pt-sans-caption-text(24px);
          font-weight: 700;
          line-height: 32px;
          color: $color-text;
          margin: 0 0 24px;
        }

        .changing-tasks__current-ul {
          display: flex;
          justify-content: space-between;
          list-style-type: none;

          .changing-tasks__current-li {
            @include pt-sans-caption-text(14px);
            font-weight: 700;
            line-height: 24px;
            padding: 12px 24px 12px 56px;
            border-radius: 50px;
            border: 1px solid $color-border;
            background-color: transparent;
            color: $color-text;

            .changing-tasks__current-li-icon-1 {
              position: relative;

              strong {
                position: relative;

                &::after {
                  @include icon-dot($color-blue);
                }
              }

              &::after {
                @include icon-circle($color-blue);
              }

              &::before {
                @include icon-stick($color-blue);
              }
            }

            .changing-tasks__current-li-icon-2 {
              position: relative;

              strong {
                position: relative;

                &::after {
                  @include icon-dot($color-orange);
                }
              }

              &::after {
                @include icon-circle($color-orange);
              }

              &::before {
                @include icon-stick($color-orange);
              }
            }

            .changing-tasks__current-li-icon-3 {
              position: relative;

              strong {
                position: relative;

                &::after {
                  @include icon-dot($color-green);
                }
              }

              &::after {
                @include icon-circle($color-green);
              }

              &::before {
                @include icon-stick($color-green);
              }
            }
          }
        }
      }

      .changing-tasks__add {
        border-radius: 48px;
        background-color: $color-white;
        padding: 40px 24px;
        max-width: 588px;
        width: 100%;

        .changing-tasks__add-title {
          @include pt-sans-caption-text(24px);
          font-weight: 700;
          line-height: 32px;
          color: $color-text;
          margin: 0 0 24px;
        }

        .changing-tasks__add-form {
          display: flex;
          justify-content: space-between;

          &-button {
            width: 44px;
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

          &-input {
            @include pt-sans-caption-text(14px);
            line-height: 24px;
            font-weight: 400;
            max-width: 478px;
            width: 100%;
            border-radius: 100px;
            padding: 12px 0 12px 16px;
            border: 1px solid $color-border;
          }
        }
      }
    }

    .changing-tasks-list__position {
      background-color: $color-white;
      padding: 40px;
      max-width: 1200px;
      width: 100%;
      border-radius: 48px;

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
    }
  }
}

.wrapper-view-tasks {
  width: 100%;
  max-width: 1200px;
  margin: 60px auto;

  &__title {
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
}

.footer{
  width: 100%;
  background: $color-dark-gray;
  height: 148px;
  border-radius: 48px 48px 0 0;
}
</style>
