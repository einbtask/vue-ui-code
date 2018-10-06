<template>
    <div class="message d-flex" :class="{unread: !item.read}">
        <img width="50px" height="50px" class="rounded-circle mr-4" :src="item.userImg" alt="user">
        <div>
            <p><strong>{{ item.userName }}</strong><span class="gray"> {{ item.time }}</span></p>
            <p>{{ longMsg }}</p>
            <i class="fas fa-reply mr-2 gray"></i><i class="fas fa-cog gray"></i>
        </div>
    </div>
</template>
<script>
export default {
    props: ['item'],
    computed:{
        longMsg(){
            let textArr = (this.item.msg).split(' ');
            if (textArr.length > 7){
                textArr.length = 8
                return textArr.join(' ') + ' (...)';
            }else {
                return this.item.msg;
            }

        }
    }
}
</script>
<style>
.unread{
    background: #f4f5f8;
}
</style>


