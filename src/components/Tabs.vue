<template>
  <ul class="tabs" :class="{[classPrefix+'-tabs']:classPrefix}">
    <li v-for="item in dataSource" :key="item.value" class="tabs-item"
        :class="liClass(item)" @click="select(item)">{{ item.text }}
    </li>
  </ul>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component, Prop} from 'vue-property-decorator';
  type DataSourceItem = {
    text: string;
    value: string;
  }
  @Component
  export default class Tabs extends Vue{
    @Prop({required: true, type: Array})
    dataSource!: DataSourceItem[];
    @Prop(String)
    readonly value!: string;
    @Prop(String)
    classPrefix?: string;

    liClass(item: DataSourceItem){
      return {
        [this.classPrefix + '-tabs-item']: this.classPrefix,
        selected: item.value === this.value
      };
    }

    select(item: DataSourceItem){
      this.$emit('update:value', item.value);
    }
  }
</script>
<style lang="scss" scoped>
.tabs {
  background: #fff;
  display: flex;
  text-align: center;
  font-size: 24px;
  &-item {
    width: 50%;
    height: 64px;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    &.selected::after {
      background: #333;
      width: 80%;
      height: 4px;
      content: '';
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translateX(-50%);
    }
    &.selected::before {
      background: #fc926a;
      width: 80%;
      height: 4px;
      content: '';
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
    } 
  }
}
</style>