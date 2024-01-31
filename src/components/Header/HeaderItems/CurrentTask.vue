<template>
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
</template>

<style lang="scss" scoped>
@import '@/common/varibles';
@import '@/common/mixins';

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

@media screen and (max-width: 1190px) {
  .changing-tasks__current {
    max-width: none;
    margin: 0 0 60px;
  }
}

@media screen and (max-width: $tablet) {
  .changing-tasks__current {
    .changing-tasks__current-title {
      @include pt-sans-caption-text(18px);
      line-height: 26px;
      margin: 0 0 24px;
    }
  }
}

@media screen and (max-width: $phone) {
  .changing-tasks__current {
    padding: 24px;

    .changing-tasks__current-ul {
      flex-direction: column;
      align-items: center;

      .changing-tasks__current-li {
        @include pt-sans-caption-text(14px);
        width: 100%;
        text-align: center;
        margin: 0 0 16px;
      }

      .changing-tasks__current-li:last-child{
        margin: 0;
      }
    }
  }
}
</style>
