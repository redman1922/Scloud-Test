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
      <div></div>
    </div>
  </div>
  <div class="wrapper-view-tasks">
    <h2>Доска задач</h2>
    <div></div>
  </div>
  <footer></footer>
</template>

<style lang="scss" scoped>
@import './common/varibles';
@import './common/mixins';

.wrapper-changing-tasks {
  background-color: $color-gray;
  padding: 64px 0 0 0;

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
  }
}
</style>
