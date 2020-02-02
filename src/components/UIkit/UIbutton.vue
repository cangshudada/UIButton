<template>
  <button
    class="ui-btn"
    :class="{
    // size
    'ui-btn-mini': mini,
    'ui-btn-small': small,
    'ui-btn-large': large,
    'ui-btn-xlarge': xlarge,

    // radius
    'ui-btn-tile': tile,
    'ui-btn-rounded': rounded,
    'ui-btn-circle': circle,

    // disabled
    'ui-btn-disabled': disabled,
  }"
    @click="onClick"
  >
    <slot></slot>
  </button>
</template>

<script lang='ts'>
import { Vue, Component, Emit, Prop } from "vue-property-decorator";

@Component
export default class UIbutton extends Vue {
  // size
  @Prop(Boolean) private mini: boolean | undefined;
  @Prop(Boolean) private small: boolean | undefined;
  @Prop(Boolean) private large: boolean | undefined;
  @Prop(Boolean) private xlarge: boolean | undefined;

  // radius
  @Prop(Boolean) private tile: boolean | undefined;
  @Prop(Boolean) private rounded: boolean | undefined;
  @Prop(Boolean) private circle: boolean | undefined;

  // disabled
  @Prop(Boolean) private disabled: boolean | undefined;

  // 传递点击事件
  @Emit("click") private emitClickEvent(event: MouseEvent) {}

  private mounted() {}

  private onClick(event: MouseEvent) {
    this.emitClickEvent(event);
  }
}
</script>

<style scoped lang='stylus'>
resize (minWidth, height, padding, fontSize) {
  min-width: minWidth;
  height: height;
  padding: 0 padding;
  font-size: fontSize;

  // &.ui-btn-rounded, &.ui-btn-circle {
  //   border-radius: (@height / 2);
  // }

  // &.ui-btn-circle {
  //   padding: 0;
  //   min-width: 0;
  //   width: @height;
  // }
}

.ui-btn {
  border: 0 solid black;
  color: #17233d;
  background-color: #2d8cf0;
  border-radius: 4px;
  outline: none;
  font-weight: 500;
  letter-spacing: 0.09em;
  cursor: pointer;
  user-select: none;
  resize(64px, 36px, 16px, 0.875rem);
  &.ui-btn-mini {
    resize(36px, 20px, 9px, 0.625rem);
  }

  &.ui-btn-small {
    resize(50px, 28px, 12px, 0.75rem);
  }

  &.ui-btn-large {
    resize(78px, 44px, 19px, 0.75rem);
  }

  &.ui-btn-xlarge {
    resize(92px, 52px, 23px, 1rem);
  }

  &.ui-btn-tile {
    border-radius: 0px;
  }
}
</style>

