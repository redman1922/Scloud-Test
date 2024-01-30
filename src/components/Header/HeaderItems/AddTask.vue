<template>
  <div class="changing-tasks__add">
    <h3 class="changing-tasks__add-title">Добавить задачу</h3>
    <form class="changing-tasks__add-form">
      <button class="changing-tasks__add-form-button" />
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


</style>