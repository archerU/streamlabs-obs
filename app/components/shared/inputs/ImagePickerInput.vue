<template>
  <div class="widget-layout-picker">
    <div
      v-for="option in metadata.options"
      :key="option.value"
      class="widget-layout-picker__option"
      :class="[value === option.value ? 'active' : '']"
      @click="emitInput(option.value)"
    >
      <img v-if="!metadata.isIcons" :src="option.description" />
      <i v-if="metadata.isIcons" :class="option.description" />
    </div>
  </div>
</template>

<script lang="ts" src="./ImagePickerInput.vue.ts"></script>

<style lang="less" scoped>
@import '../../../styles/index';

.widget-layout-picker {
  width: 100%;
  max-width: 370px;
  display: grid;
  grid-template-columns: repeat(auto-fit, 56px);
  grid-column-gap: 4px;
  grid-row-gap: 4px;
}

.widget-layout-picker__option {
  .radius();

  width: 56px;
  height: 56px;
  border: 1px solid var(--solid-input);
  background-color: var(--solid-input);
  position: relative;
  cursor: pointer;

  img,
  i {
    height: 48px;
    font-size: 48px;
    color: var(--title);
    width: auto;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  &.active {
    background-color: var(--link-active);
    border-color: var(--link-active);

    i {
      color: var(--background);
    }
  }
}
</style>
