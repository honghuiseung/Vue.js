<!-- WishFooter.vue -->
<template lang="html">
    <div class="clearAllContainer">
        <span class="clearAllBtn" @click="clickRemove">Clear All</span>
    </div>

    <modal @close="showModal = false">
        <!-- 모달 제목 -->
        <h3 slot="header">경고</h3>
        <!-- 모달 내용 -->
        <span slot="footer" @click="showModal = false">
            정말로 삭제 하시겠습니까?
            <i aria-hidden="true" @click="clearWish">삭제</i>
            <i aria-hidden="true">취소</i>
        </span>
    </modal>
</template>
<script>
    import Modal from './common/Modal.vue'

    export default{
        data(){
            return{
                showModal: false
            }
        },
        methods:{
            clearWish(){
                this.$emit('removeAll');

            },
            clickRemove(){
                this.showModal = !this.showModal;
            }
        },
        components:{
          Modal: Modal
        }
    }
</script>
<style lang="css" scoped>
    .clearAllContainer{width: 7.5em; height: 50px; line-height: 50px; background: linear-gradient(to right, #ff4c4d, #b30000); border-radius: 5px; margin: 25px auto 0px;}
    .clearAllBtn{font-weight: bold; text-transform: uppercase; letter-spacing: -1px; color: white; display: block; cursor: pointer;}
</style>
