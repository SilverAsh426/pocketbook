<template>
  <div class="tags">
    <div class="new">
      <button @click="create">新增标签</button>
    </div>
    <ul class="current">
      <li v-for="tag in dataSource" :key="tag"
          :class="{selected: selectedTags.indexOf(tag)>=0}"
          @click="toggle(tag)">{{tag}}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component, Prop} from 'vue-property-decorator';

  @Component
  export default class Tags extends Vue {
    @Prop() readonly dataSource: string[] | undefined;
    selectedTags: string[] = [];

    toggle(tag: string){
      const index = this.selectedTags.indexOf(tag)
      if (index >= 0){
        this.selectedTags.splice(index, 1)
      }else{
        this.selectedTags.push(tag)
      }
      this.$emit('update:value', this.selectedTags)
    }
    create(){
      const  name = window.prompt('请输入需要添加的标签名')
      if (name === ''){
        window.alert('标签名不能为空')
      }else {
        if (this.dataSource){
          this.$emit('update:dataSource', [...this.dataSource, name])
        }
      }
    }
}
</script>

<style lang="scss" scoped>
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
      $bg : rgb(221,232,246);
      background: $bg;
      height: 24px;
      line-height: 24px;
      border-radius: 12px;
      padding: 0 18px;
      margin-right: 12px;
      margin-top: 4px;
      &.selected{
        background: darken($bg, 15%);
        color: white;
      }
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
</style>