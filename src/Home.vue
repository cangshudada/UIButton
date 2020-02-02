<template>
  <div id="home">
    <div class="btn-container">
      <UIButton
        @click="onClick"
        :mini="mini"
        :small="small"
        :medium="medium"
        :large="large"
        :xlarge="xlarge"
        :tile="tile"
        :rounded="rounded"
        :circle="circle"
      >Hello</UIButton>
    </div>
    <div class="btn-group">
      <UIButton class="btn" @click="resize('mini')">超小</UIButton>
      <UIButton class="btn" @click="resize('small')">小</UIButton>
      <UIButton class="btn" @click="resize('medium')">正常</UIButton>
      <UIButton class="btn" @click="resize('large')">大</UIButton>
      <UIButton class="btn" @click="resize('xlarge')">超大</UIButton>
    </div>

    <div class="btn-group">
      <UIButton class="btn" @click="changeRedius('tile')">方形</UIButton>
      <UIButton class="btn" @click="changeRedius('normal')">正常</UIButton>
      <UIButton class="btn" @click="changeRedius('rounded')">半圆形</UIButton>
      <UIButton class="btn" @click="changeRedius('circle')">圆形</UIButton>
    </div>
  </div>
</template>

<script lang='ts'>
import { Vue, Component } from "vue-property-decorator";
import UIButton from "@/components/UIkit/UIbutton.vue";

@Component({
  components: {
    UIButton
  }
})
export default class Home extends Vue {
  private mini: boolean = false;
  private small: boolean = false;
  private medium: boolean = true;
  private large: boolean = false;
  private xlarge: boolean = false;

  private tile: boolean = false;
  private rounded: boolean = false;
  private normal: boolean = true;
  private circle: boolean = false;

  private onClick(event: MouseEvent) {
    console.log("hello");
  }

  private resize(name: string) {
    this.mini = false;
    this.small = false;
    this.medium = false;
    this.large = false;
    this.xlarge = false;
    switch (name) {
      case "mini":
        this.mini = true;
        break;
      case "small":
        this.small = true;
        break;
      case "medium":
        this.medium = true;
        break;
      case "large":
        this.large = true;
        break;
      case "xlarge":
        this.xlarge = true;
        break;
    }
  }

  private changeRedius(radius: string) {
    this.tile = false;
    this.rounded = false;
    this.normal = false;
    this.circle = false;
    switch (radius) {
      case "tile":
        this.tile = true;
        break;
      case "rounded":
        this.rounded = true;
        break;
      case "normal":
        this.normal = true;
        break;
      case "circle":
        this.circle = true;
        break;
    }
  }
}
</script>

<style scoped lang='stylus'>
.btn-container {
  width: 480px;
  height: 160px;
  margin: 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
}
.btn {
  margin: 6px;
}
</style>
