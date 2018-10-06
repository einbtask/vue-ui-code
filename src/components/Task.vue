<template>
    <div class="task d-flex">
        <div class="first-letter mr-4">{{ item.title | firstLetter }}</div>
        <div class="d-flex flex-column">
            <h6>{{ item.title }}</h6>
            <span class="gray" :class="{delay: delayed}"><i class="far fa-clock"></i> {{ item.time }}</span>
        </div>
        <i class="fas fa-ellipsis-v gray"></i>
    </div>
</template>
<script>
export default {
    data(){
        return{
            delayed: false
        }
    },
    props: ['item'],
    filters:{
        firstLetter(text){
            return text.charAt(0);
        }
    },
    created(){
        if ((this.item.time).includes("delays")){
            this.delayed = true;
            this.$emit('delayCounter');
        }
    }
}
</script>
<style scoped>
.first-letter{
    background: #5584ff;
    border-radius: 50%;
    color: white;
    font-size: 1.5rem;
    min-width: 50px;
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.delay{
    color: #f83c7b;
}
.task{
    position: relative;
    padding-right: 2.5rem;
}
.fa-ellipsis-v{
    position: absolute;
    right: 1.5rem;
    font-size: 2.5rem;
    -webkit-text-stroke: 5px white;
}
</style>


