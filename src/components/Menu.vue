<template>
    <div class="menu">
        <div class="logo pl-4">
            <img src="https://res.cloudinary.com/einat/image/upload/v1538801830/logo.png" alt="merkury logo">
        </div>
        <button> <span class="plus">+</span> Add project</button>
        <nav class="d-flex flex-column">
            <div v-for="(item, index) of menuItems" :key="index" class="nav-item d-flex pt-4 pb-4 pl-4 align-items-center">
                <img :src="item.icon" :alt="item.name" class="mr-3" width="25px" height="25px">
                <h3>{{item.name}}</h3>
                <div class="overlay"></div>
            </div>
        </nav>
    </div>
</template>

<script>
export default {
    props: ['menuItems']
}
</script>

<style scoped>
.menu{
    width:17%;
    min-width: 260px;
    background: #0e1a35;
    color: white;
    display: flex;
    flex-direction: column;
}
.logo{
    padding-top: 1.5rem; 
    padding-bottom: 1.5rem; 
}
.nav-item{
    border: 1px solid #0d172e;
    position: relative;
}
.overlay {
  width: 100%;
  height: 100%;
  transition: .3s ease;
  opacity: 0;
  border-left: 8px solid #5584ff;
  box-sizing: border-box;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.nav-item:hover{
    background-color: #122143;
}
.nav-item:hover .overlay{
    opacity: 1;
}
button{
    display: none;
    width: 140px;
    margin: 1rem auto;
}
@media only screen and (max-width: 990px) {
    button{
    display: block;
    }
}
</style>

