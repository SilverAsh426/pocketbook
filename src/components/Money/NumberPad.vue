<template>
  <div class="numberPad">
    <div class="output">{{ output }}</div>
    <div class="buttons">
      <button @click="inputContent">1</button>
      <button @click="inputContent">2</button>
      <button @click="inputContent">3</button>
      <button @click="remove">退格</button>
      <button @click="inputContent">4</button>
      <button @click="inputContent">5</button>
      <button @click="inputContent">6</button>
      <button @click="clear">清空</button>
      <button @click="inputContent">7</button>
      <button @click="inputContent">8</button>
      <button @click="inputContent">9</button>
      <button @click="ok" class="ok">OK</button>
      <button @click="inputContent">.</button>
      <button @click="inputContent" class="zero">0</button>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component, Prop} from 'vue-property-decorator';

@Component
export default class NumberPad extends Vue {
  @Prop(Number) readonly value!: number;
  output = this.value.toString();

  inputContent(event: MouseEvent) {
    const button = (event.target as HTMLButtonElement);
    const input = button.textContent!;
    if (this.output.length === 16) {return;}
    if (this.output === '0') {
      if ('0123456789'.indexOf(input) >= 0) {
        this.output = input;
      } else {
        this.output += input;
      }
      return;
    }
    if (this.output.indexOf('.') >= 0 && input === '.') {return;}
    this.output += input;
  }

  remove() {
    if (this.output.length === 1) {
      this.output = '0';
    } else {
      this.output = this.output.slice(0, -1);
    }
  }

  clear() {
    this.output = '0';
  }

  ok() {
    const number = parseFloat(this.output);
    this.$emit('update:value', number);
    this.$emit('submit', number);
    this.output = '0';
  }
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/helper.scss";

.numberPad {
  .output {
    font-size: 36px;
    font-family: Consolas, monospace;
    padding: 9px 16px;
    text-align: right;
    height: 72px;
    box-shadow: inset 0 -5px 5px -5px fade_out(rgb(181, 204, 236), 0.2),
    inset 0 5px 5px -5px fade_out(rgb(181, 204, 236), 0.2);
  }

  .buttons {
    @extend %clearFix;
    font-family: $font-hei;
    font-size: 18px;

    > button {
      width: 25%;
      height: 64px;
      float: left;
      background: transparent;
      border: none;

      &.ok {
        height: 128px;
        float: right;
      }

      &.zero {
        width: 50%;
      }

      $bg: rgb(120, 163, 220);

      &:nth-child(12) {
        background: $bg;
      }

      &:nth-child(14) {
        background: lighten($bg, 5%);
      }

      &:nth-child(8), &:nth-child(11), &:nth-child(13) {
        background: lighten($bg, 10%);
      }

      &:nth-child(4), &:nth-child(7), &:nth-child(10) {
        background: lighten($bg, 15%);
      }

      &:nth-child(3), &:nth-child(6), &:nth-child(9) {
        background: lighten($bg, 20%);
      }

      &:nth-child(2), &:nth-child(5) {
        background: lighten($bg, 25%);
      }

      &:nth-child(1) {
        background: lighten($bg, 29%);
      }
    }
  }
}
</style>