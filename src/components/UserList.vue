<template>
    <div class="wrapper">
    <md-toolbar class="md-transparent" md-elevation="0">
       <p>Users list </p>
    </md-toolbar>
    <div class="user-list">
            <UserItem v-for="(user, i) in users" :user="user" :index="(i+1)" @viewDetails="viewDetails(i)" />
        </div>
    </div>
</template>

<script>
import Avatar from 'vue-avatar-component'
import _ from 'lodash';

export default {
  components: { 
   Avatar,
    UserItem: () => import('./UserItem')
  },
  props:{},
  data () {
    return {
      users: {},
    }
  },
  mounted () {
    fetch('https://randomuser.me/api/?results=20&nat=us')
    .then((response) => {
      return response.json()
    })
    .then((data) => {
      this.users = data.results
    })
  },
  methods:{
      viewDetails(id){
      let userToView = this.users[id];
      this.$emit("viewDetails", userToView);
    }
  }
}
</script>

<style lang="scss">
.md-drawer.md-permanent{
    max-width: 245px;
    width: 100%;
}
.add-info{
    padding: 10px;
}
.md-card-actions.md-alignment-right{
    justify-content: flex-end;
}
.md-app{
    max-width: 1100px;
    margin: 0 auto;
}
.md-card-header{
    padding: 10px;
}
.md-title p{
    font-size: 16px;
    font-weight: 500;
}
.md-elevation-4{
    box-shadow: none;
}
.md-card-content{
    text-align: center;
}
.user-id span{
    font-weight: 500;
}
.md-card-content{
    padding: 0px;
}
.md-drawer.md-permanent{
  padding-right:30px;
}
.md-transparent p{
  font-size: 20px;
}
.user-list{
  max-height: 400px;
  overflow-y: scroll;
}
::-webkit-scrollbar { width: 3px; height: 3px;}
::-webkit-scrollbar-track-piece { background-color: #eaeaea;}
::-webkit-scrollbar-thumb { height: 50px; background-color: #7ac4ff; border-radius: 3px;}
.user-list .wrapper{
  margin: 0 10px;
}
</style>