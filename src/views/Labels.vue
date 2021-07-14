<template>
  <Layout>
    <div class="tags">
      <router-link class="tag"
                   v-for="tag in tags" :key="tag.id"
                   :to="`/label/edit/${tag.id}`">
        <span>{{tag.name}}</span>
        <Icon name="right"/>
      </router-link>
    </div>
    <div class="createTag-wrapper">
      <Button class="createTag" @click="createTag">+</Button>
    </div>
  </Layout>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component} from 'vue-property-decorator';
import Button from '@/components/Button.vue';
import {mixins} from 'vue-class-component';
import TagHelper from '@/mixins/TagHelper';

@Component({
  components:{Button}
})
export default class Labels extends mixins(TagHelper){
  get tags(){
    return this.$store.state.tagList;
  }
  beforeCreate(){
    this.$store.commit('fetchTags');
  }
}
</script>

<style lang="scss" scoped>
.tags {
  font-size: 16px;
  padding: 16px;
  > .tag {
    background: #fff;
    min-height: 44px;
    margin-bottom: 16px;
    padding-left: 15px;
    border: 1px solid #343434;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    svg {
      width: 18px;
      height: 18px;
      color: #666;
      margin-right: 16px;
    }
  }
}
.createTag {
  background: #767676;
  color: white;
  border-radius: 50%;
  font-size: 40px;
  border: none;
  height: 60px;
  width: 60px;
  &-wrapper {
    position: absolute;
    right: 0;
    bottom: 60px;
    text-align: center;
    padding: 16px;
    margin-top: 44-16px;
  }
}
</style>