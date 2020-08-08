<template>
  <Layout class-prefix="layout">
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
    <div>
      <ul class="types">
        <li class="selected">支出</li>
        <li>收入</li>
      </ul>
    </div>
    <div>
      <label class="notes">
        <span class="name">备注</span>
        <input type="text" placeholder="在这里输入内容">
      </label>
    </div>
    <div class="tags">
      <div class="new">
        <button>新增标签</button>
      </div>
      <ul class="current">
        <li>服饰</li>
        <li>餐饮</li>
        <li>房租</li>
        <li>出行</li>
      </ul>
    </div>
  </Layout>
</template>

<script lang="ts">
  export default {
    name: 'Money'
  };
</script>

<style lang="scss">
  .layout-content {
    display: flex;
    flex-direction: column-reverse
  }
</style>

<style lang="scss" scoped>
  @import "~@/assets/style/helper.scss";

  .tags {
    flex-grow: 1;
    font-size: 14px;
    padding: 16px;
    display: flex;
    flex-direction: column-reverse;

    > .current {
      display: flex;
      flex-wrap: wrap;

      > li {
        background: #d9d9d9;
        height: 24px;
        line-height: 24px;
        border-radius: 12px;
        padding: 0 18px;
        margin-right: 12px;
        margin-top: 4px;
      }
    }

    > .new {
      padding-top: 16px;

      button {
        background: transparent;
        border: none;
        color: #999;
        border-bottom: 1px solid;
        padding: 0 4px;
      }
    }
  }

  .notes {
    font-size: 14px;
    display: flex;
    background: #f5f5f5;
    padding-left: 16px;
    align-items: center;

    .name {
      padding-right: 16px;
      font-size: 18px;
    }

    input {
      height: 64px;
      flex-grow: 1;
      background: transparent;
      border: none;
      padding-right: 16px;
    }
  }

  .types {
    background: #c4c4c4;
    display: flex;
    text-align: center;
    font-size: 24px;

    > li {
      width: 50%;
      height: 64px;
      display: flex;
      justify-content: center;
      align-items: center;
      background: ghostwhite;

      &.selected{
        content: '';
        background: rgb(100, 149, 215);
        color: whitesmoke;
      }
    }
  }

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