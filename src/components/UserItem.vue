<template>
     <div class="wrapper">
            <md-card class="list-cart">
            <div class="list-cart__wrap">
                <md-card-header>
                <avatar :image="user.picture.medium" :size="80"/>
            </md-card-header>
            <md-card-content>
                <p>{{ user.name.first }} {{ user.name.last }}</p>
                <div class="user-id">
                    <p><span>ID: </span> {{ user.id.value }}</p>
                </div>
            </md-card-content>
            </div>
            <md-card-actions>
                  <md-button @click="viewDetailsClicked">Show more</md-button>
            </md-card-actions>
      </md-card>
      </div>
</template>
<script>
import Avatar from 'vue-avatar-component'
export default {
    components:{
        Avatar
    },
  props:{
    user: {
      type: Object,
      default(){
        return {}
      }
    },
    index:{
      type: Number
    }
  },
  data(){
    return{}
  },
  methods:{
    viewDetailsClicked(){
      this.$emit("viewDetails",  this.user.id.value);
    }
  }
}
</script>

<style lang="scss"  scoped>
.list-cart .md-card-header,
.md-card-content:last-of-type{
    padding: 0px;
}
.user-list .list-cart .avatar{
    width: 50px !important;
    height: 50px !important;
}
.list-cart__wrap{
  display: flex;
}
.md-card-header{
  margin-right: 15px;
}
.md-card{
  margin-bottom: 10px;
  padding: 10px 5px;
}
.md-card-content p{
  margin: 0px;
}
</style>