<template>
  <div class="yellow lighten-3 pa-3">
    <h3>회원 정보를 수정할 수 있습니다.</h3>
    <p>수정사항</p>
      <v-text-field
        v-model="user.name"
        labe="이름"
      ></v-text-field>
      <v-text-field
        v-model="user.address"
        labe="주소"
      ></v-text-field>
      <v-text-field
        v-model="user.phone"
        labe="전화번호"
      ></v-text-field>
      <v-radio-group v-model="user.hasDog">
        <v-radio
          label="'반련견 있음'"
          :value="true"
        ></v-radio>
        <v-radio
          label="'반련견 있음'"
          :value="false"
        ></v-radio>
        <v-btn @click="changeUser">수정 완료</v-btn>
      </v-radio-group>
  </div>
</template>

<script>
  export default{
    props: ['name', 'address', 'phone', 'hasDog'],
    data() {
      return {
        //자식 component에서 가공한 다음 text-field에 넣어준다
        user:{}
      }
    },
    //component가 created될 때 그 값을 user:{}안에 넣어준다.
      created() {
        this.user.name = this.name
        this.user.address = this.address
        this.user.phone = this.phone
        this.user.hasDog = this.hasDog
      },
      methods: {
        changeUser(){
          console.log(this.user)
          //부모component에 this.user를 보내준다
          this.$emit('child', this.user)
        }
      }
  }
</script>
