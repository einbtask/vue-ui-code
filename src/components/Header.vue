<template>
    <header>
        <div class="header-left">
            <div v-show="arrow" class="arrow-left mr-1"></div>
            <i @click="toggleMenu" class="fas fa-bars mr-4"></i>
            <i class="fas fa-search"></i>
        </div>
        <div class="header-right">
            <button> <span class="plus">+</span> Add project</button>
            <i class="fas fa-envelope mr-4"></i>
            <div class="alerts-main mr-4">
                <i class="fas fa-bell"></i>
                <span class="alerts">{{alerts}}</span>
            </div>
            <img :src="imgUrl" class='rounded-circle mr-2' width='50px' height='50px'>
            <div class="arrow-down"></div>
        </div>
    </header>
</template>

<script>
export default {
    props: ['alerts', 'imgUrl', 'arrow'],
    methods:{
        toggleMenu(){
            this.$emit('changeMenu');
        }
    }
}
</script>

<style scoped>
.header-left, .header-right{
    display: flex;
    width: auto;
    max-width: 50%;
    align-items: center;
}
header {
    padding: 1rem 2rem;
    display: flex;
    justify-content: space-between;
    background: white;
    border-bottom: 1px solid #d4d9e3;
}
.fas{
 font-size: 1.2rem;
}
.arrow-down{
  width: 0; 
  height: 0; 
  border-left: 7px solid transparent;
  border-right: 7px solid transparent;
  border-top: 7px solid black;
}

.arrow-left{
  width: 0; 
  height: 0; 
  border-right: 5px solid #5584ff;
  border-bottom: 5px solid transparent;
  border-top: 5px solid transparent;
}
.alerts-main{
    position: relative;
    width: 17px;
}
.alerts{
    width: 20px;
    height: 20px;
    border: white solid 1px;
    background-color: #5584ff;
    font-size: 0.8rem;
    color: white;
    border-radius: 50%;
    position: absolute;
    top: -10px;
    right: -13px;
    display: flex;
    justify-content: center;
    align-items: center;
}
@media only screen and (max-width: 990px) {
    button{
        display: none;
    }
}
</style>
