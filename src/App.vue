<template>
  <div id="app">
    <transition name="slide-fade">
      <Menu class="menu-toggle" v-show="isOpen" :menuItems="menuItems"/>
    </transition>
    <main class="d-flex flex-column">
      <Header :imgUrl="user.imgUrl" :alerts="user.alerts" @changeMenu="toggleMenu" :arrow="isOpen"/>
      <div class="main-container">
        <h1 class="pt-4">Hello {{user.name}}!</h1>
        <div class="images d-flex justify-content-between">
          <div class="sales"><img class="img-fluid" :src="user.charts[0]" alt="sales"></div>
          <div class="report"><img class="img-fluid" :src="user.charts[1]" alt="report"></div>
        </div>
        <div class="dashboard w-100 justify-content-between mt-5 mb-5">
          <List :title="'tasks'" :info="user.tasks" :counter="5"/>
          <List :title="'messages'" :info="user.messages" :counter="2"/>
          <List :title="'activity'" :info="user.activities" :counter="10"/>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Menu from './components/Menu.vue'
import List from './components/List.vue'

const imgCloud = "https://res.cloudinary.com/einat/image/upload/"

export default {
  data(){
    return{
      isOpen: false,
      menuItems:[
                {icon: imgCloud + "v1538768721/home_03.png", name:"Home"},
                {icon: imgCloud + "v1538768720/workflow.png", name:"Workflow"},
                {icon: imgCloud + "v1538768720/statistics.png", name:"Statistics"},
                {icon: imgCloud + "v1538768721/calendar.png", name:"Calendar"},
                {icon: imgCloud + "v1538768721/users.png", name:"Users"},
                {icon: imgCloud + "v1538768721/settings.png", name:"Settings"}
            ],
      user: {
        name: "John",
        imgUrl: imgCloud + "v1538768720/john.jpg",
        alerts: 3,
        charts:[imgCloud + "v1538768721/sales.jpg", imgCloud +"v1538768721/report.jpg"],
        tasks:[
          {title: "New Website for Symu.co", time: "5 days delays"},
          {title: "Free business PSD Template", time: "2 days delays"},
          {title: "New logo for JCD.pl", time: "5 days left"},
          {title: "Free Icons Se vol. 3", time: "10 days left"}
        ],
        messages:[
          {userImg: "https://res.cloudinary.com/einat/image/upload/v1538768720/jones.jpg", userName: "Nina Jones", time:"5 minutes ago", msg:"Hey you it's me again:-) I attached new lorem lorem lorem", read: false},
          {userImg: "https://res.cloudinary.com/einat/image/upload/v1538768720/jones.jpg", userName: "Nina Jones", time:"About 20 hours ago", msg:"Hey! I attached some new PSD files for lorem lorem lorem", read: false},
          {userImg: "https://res.cloudinary.com/einat/image/upload/v1538768720/smith.jpg", userName: "James Smith", time:"2 days ago", msg:"Good morning, you are fired!", read: true},
          {userImg: "https://res.cloudinary.com/einat/image/upload/v1538768720/jones.jpg", userName: "Nina Jones", time:"About 2 weeks ago", msg:"Hello! Could you bring me coffee please?", read: true}
        ],
        activities:[
          {userImg: imgCloud + "v1538768720/jones.jpg", userName: "Nina Jones", action:"added a new project", subject:"Free UI Kit", time:"Just now"},
          {userImg: imgCloud + "v1538768720/smith.jpg", userName: "James Smith", action:"commented project", subject:"Free PSD Template", time:"40 minutes ago"},
          {userImg: imgCloud + "v1538768720/jones.jpg", userName: "Nina Jones", action:"completed task", subject:"Symu Website", time:"1 hour ago"},
          {userImg: imgCloud + "v1538818273/spears.jpg", userName: "Alexandra Spears", action:"added a new project", subject:"Free PSD (...)", time:"3 hours ago"}
        ]
      }
    }
  },
  name: 'app',
  components: {
    Header,
    Menu,
    List
  },
  methods: {
    toggleMenu(){
      this.isOpen = !this.isOpen;
    }
  }
}
</script>

<style>
#app{
  display: flex;
}
body{
  font-size: 12px;
}
.total-flex{
  display: flex;
  justify-content: center;
  align-items: center;
}
.gray{
    color: #8492af;
}
.dashboard{
  display: flex;
}

main{
  background: #f6f7fa;
  width:100%;
  transition: all .10s ease;
}

h1{
  height: 10vh;
}
.sales{
  width: 37%;
}
.report{
  width: 56.5%;
}
.main-container{
  padding: 0 2rem;
}
.slide-fade-enter-active {
  transition: all .1s ease;
}
.slide-fade-leave-active {
  transition: all .1s ease;
}
.slide-fade-enter, .slide-fade-leave-to{
  opacity: 0;
  transform: translateX(-100%);
}
article{
  background: white;
  border: #d4d9e3 1px solid;
  border-bottom: none;
  width: 30%;
  position: relative;
}
.task, .message, .activity{
  border-bottom: #d4d9e3 1px solid;
  height: 100px;
  padding: 0 1.5rem;
  display: flex;
  align-items: center;
}
h3, h4, p{
  margin-bottom: 0;
}
button{
    border: none;
    box-shadow: none;
    color: white;
    background-color: #5584ff;
    padding: 0.4rem 1.5rem;
    border-radius: 2rem;
    box-sizing: border-box;
    text-decoration: none;
    margin-right: 3rem;
}
.plus{
    color: #aac2ff;
}

@media only screen and (max-width: 1200px) {
  .dashboard{
    flex-direction: column;
  }
  article{
    width: 100%;
    margin-bottom: 2rem;
  }
}

@media only screen and (max-width: 990px) {
  .images{
    flex-direction: column;
    align-items: center;
  }
  .sales, .report{
    width: 80%;
    margin-bottom: 1rem;
  }
  h1{
    font-size: 1.5rem;
  }
}
</style>
