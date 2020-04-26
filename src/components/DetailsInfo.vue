<template>
        <md-card class="list-cart">
          <div class="details-wrap">
            <avatar :image="user.picture.medium" :size="100"/>
            <div class="details-wrap__info">
              <p><span>Adress:</span> {{user.location.city}}, {{user.location.street.name}}, {{user.location.street.number}}</p>
              <p><span>E-mail :</span> {{user.email}}</p>
              <p><span>Gender :</span> {{user.gender}}</p>
              <p><span>Dob :</span> {{user.dob.date}}</p>
              <p><span>Phone number: </span> {{user.phone}}</p>
            </div>
          </div>
        </md-card>
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
    }
  },
  data(){
    return{}
  }
}
</script>

<style lang="scss">
span{
  font-weight: 600;
}
.details-wrap{
  display: flex;
  .details-wrap__info{
    margin-left: 20px;
  }
}
.md-app-content .md-card{
  width: 100%;
  padding: 30px;
}
</style>