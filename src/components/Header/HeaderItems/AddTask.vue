<template>
  <div class="changing-tasks__add">
    <h3 class="changing-tasks__add-title">Добавить задачу</h3>
    <form class="changing-tasks__add-form">
      <button class="changing-tasks__add-form-button">Добавить задачу</button>
      <input placeholder="Текст" class="changing-tasks__add-form-input" />
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

@media screen and (max-width: 1190px) {
  .changing-tasks__add {
    max-width: none;

    .changing-tasks__add-form{
      &-button {
        width: 48px;

      }
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
    .changing-tasks__add-title {
      @include pt-sans-caption-text(18px);
      line-height: 26px;
      margin: 0 0 24px;
    }
  }
}


@media screen and (max-width: $phone) {
  .changing-tasks__add {
    padding: 24px;

    .changing-tasks__add-form{
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
      &-input {
        @include pt-sans-caption-text(14px);
        max-width: none;
        margin: 0 0 24px;
      }
    }
  }
}

</style>