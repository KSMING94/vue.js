<template>
  <div class="blue lighten-3 pa-3">
    <h1>User 컴포넌트</h1>
    <p>이름: 뷰제이에스</p>
    <hr>
    <v-layout row wrap>
      <v-flex xs12 sm6>
        <UserDetail
          :name="name"
          :address="address"
          :phone="phone"
          :hasDog="hasDog"
        >
        </UserDetail>
      </v-flex>
      <v-flex xs12 sm6>
        <!-- 자식 component로 부터 신호 받기 -->
        <UserEdit
          :name="name"
          :address="address"
          :phone="phone"
          :hasDog="hasDog"
          @child="parents"
        ></UserEdit>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import UserDetail from "./UserDetail.vue"
import UserEdit from "./UserEdit.vue"

export default {
  components: {
    UserDetail,
    UserEdit
  },
  data() {
    return {
      name: 'Hoza',
      address: 'Seoul',
      phone: '123456789',
      hasDog: true,
    }
  },
  methods : {
    parents(user) {
      //user = {name, address, phone, hasDog}
      this.name = user.name
      this.address = user.address
      this.address = user.phone
      this.hadDog = user.hasDog
      console.log('부모가 받았어')
    }
  }
}
</script>