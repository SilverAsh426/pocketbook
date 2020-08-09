<template>
  <div class="numberPad">
    <div class="output">100</div>
    <div class="buttons">
      <button>1</button>
      <button>2</button>
      <button>3</button>
      <button>退格</button>
      <button>4</button>
      <button>5</button>
      <button>6</button>
      <button>清空</button>
      <button>7</button>
      <button>8</button>
      <button>9</button>
      <button class="ok">OK</button>
      <button>.</button>
      <button class="zero">0</button>
    </div>
  </div>
</template>

<script lang="ts">
  export default {
    name: 'NumberPad'
  };
</script>

<style lang="scss" scoped>
  @import "~@/assets/style/helper.scss";
  .numberPad {
    .output {
      font-size: 36px;
      font-family: Consolas, monospace;
      padding: 9px 16px;
      text-align: right;
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