<!-- WishList.vue -->
<template lang="html">
<section>
  <!--선택한 위시리스트를 뷰에서 인식하도록 만들기 할 차례-->
  <!--npm run dev-->
  <transition-group name="list" tag="ul">
    <li v-for="(wishItem, index) in propsData" v-bind:key="wishItem" class="shadow">
      <i class="checkBtn fas fa-check" aria-hidden="true"></i>
      {{wishItem}}
      <span class="removeBtn" type="button" @click="removeWish(wishItem, index)">
        <i class="far fa-trash-alt" aria-hidden="true"></i>
      </span>
    </li>
  </transition-group>
</section>
</template>
<script>
  export default{
    props: ['propsData'],
    //data(){
    //  return{
    //    wishItems:[]
    //  }
    //},
    methods:{
      removeWish(wishItem, index){
        //console.log(wishItem, index);
        //localStorage.removeItem(wishItem);
        //this.wishItems.splice(index, 1);
        this.$emit('removeWish', wishItem, index);
      }
    }
  }
</script>
<style lang="css" scoped>
.list-enter-active, .list-leave-active{
  transition: all 1s;
}
.list-enter, .list-leave-to{
  opacity:0;
  transform: translateY(30px);
}
  ul{
    list-style-type: none;
    padding-left: 8px;
    margin-top: 0px;
    text-align: left;
  }
  li{
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5em 0;
    padding: 0 0.9em;
    background: #fefefe;
    border-radius: 5px;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .checkBtn{
    line-height: 50px;
    color: #ff8000;
    margin-right: 5px;
  }
  .removeBtn{
    margin-left: auto;
    color: #de4343;
  }
</style>
