<template>
    <article>
        <div class="article-header d-flex justify-content-between align-items-center">
            <h3>{{ title | capitalLetter }}</h3>
            <div class="counters d-flex">
                <span class="counter">{{ counter }}</span>
                <span class="counter delay-counter" v-show="delayCounter">{{ delayCounter }}</span>
            </div>
        </div>
        <div>
           <component @delayCounter="updateCounter" v-for="(item,index) in info" :item="item" :key="index" :is="title"/>
        </div>
    </article>
</template>

<script>
import tasks from './Task.vue'
import messages from './Message.vue'
import activity from './Activity.vue'

export default {
    data(){
        return{
            delayCounter: null
        }
    },
    props: ['title', 'info', 'counter'],
    components:{
        tasks,
        messages,
        activity
    },
    filters: {
        capitalLetter(text){
            return text.charAt(0).toUpperCase() + text.substr(1);
        }
    },
    methods:{
        updateCounter(){
            this.delayCounter++;
        }
    }
}
</script>

<style scoped>
.article-header{
    padding: 2rem;
    border-bottom: #d4d9e3 1px solid;
}
.counter{
    width: 45px;
    height: 45px;
    background-color: #5584ff;
    font-size: 1.25rem;
    color: white;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
}
.delay-counter{
    background-color: #f83c7b;
    margin-left: 0.5rem;
}
</style>


