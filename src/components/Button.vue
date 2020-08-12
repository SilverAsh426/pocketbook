<template>
  <button class="button" @click="$emit('click', $event)">
    <slot/>
  </button>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component} from 'vue-property-decorator'
@Component
export default class Button extends Vue{

}
</script>

<style lang= "scss" scoped>
.button {
  color: white;
  background: rgb(100, 149, 215);
  border-radius: 4px;
  border: 0 none;
  height: 40px;
  padding: 0 16px;

  &-wrapper {
    text-align: center;
    padding: 16px;
    margin-top: 28px;
  }
}
</style>