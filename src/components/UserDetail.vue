<template>
  <div class="red lighten-3 pa-3">
    <h3>자세한 회원 정보를 확인합니다.</h3>
    <p>상세사항</p>
    <v-list dense>
      <v-list-tile>
        <v-list-tile-content>이름:</v-list-tile-content>
        <v-list-tile-content class="align-end">
          {{ name }}
        </v-list-tile-content>
      </v-list-tile>
      <v-list-tile>
        <v-list-tile-content>주소:</v-list-tile-content>
        <v-list-tile-content class="align-end">
          {{ address }}
        </v-list-tile-content>
      </v-list-tile>
      <v-list-tile>
        <v-list-tile-content>전화번호:</v-list-tile-content>
        <v-list-tile-content class="align-end">
          {{ phone }}
        </v-list-tile-content>
      </v-list-tile>
      <v-list-tile>
        <v-list-tile-content>반려견유무:</v-list-tile-content>
        <v-list-tile-content class="align-end">
          {{ hasDog }}
        </v-list-tile-content>
      </v-list-tile>
      <v-list-tile>
        <v-list-tile-content>수정일자:</v-list-tile-content>
        <v-list-tile-content class="align-end">
          {{ editedDate }}
        </v-list-tile-content>
      </v-list-tile>
    </v-list>
  </div>
</template>

<script>
//UserDetail를 전달 받는 것
import { eventBus } from "../main"
export default {
  data() {
    return {
      editedDate: null
    }
  },
  props : ['name', 'address', 'phone', 'hasDog'],
  computed: {
    hasDogKr() {
      return this.hadDog === true ? '있음' : '없음'
    }
  },
  //lifecycle인 created hook을 사용해 eventListener 선언
  created() {
    eventBus.$on('userWasEdited', date => {
      this.editedDate = date
    })
  }
}
</script>

