<template>
  <div>
    <label class="notes">
      <span class="name">备注</span>
      <input type="text" placeholder="在这里输入内容">
    </label>
  </div>
</template>

<script lang="ts">
  export default {
    name: 'Notes'
  };
</script>

<style lang="scss" scoped>
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
</style>