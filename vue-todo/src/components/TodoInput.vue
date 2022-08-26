<template>
 <div class="inputBox shadow">
   <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
   <span class="addContainer" v-on:click="addTodo">
     <i class="fa-solid fa-plus"></i>
   </span>
   <modal v-if="showModal" @close="showModal = false">
     <h3 slot="header">
       경고!
       <i class="closeModalBtn fa-solid fa-calendar-xmark" @click="showModal = false"></i>
     </h3>
     <div slot="body">일정을 입력하세요.</div>
   </modal>
 </div>
</template>

<script>
import AlertModal from "@/components/common/AlertModal";

export default {
  data() {
    return {
      newTodoItem: "",
      showModal: false
    }
  },
  methods: {
    addTodo() {
      if (this.newTodoItem !== '') {
        this.$store.commit('addOneItem', this.newTodoItem);
        this.clearInput();
      } else {
        this.showModal = !this.showModal;
      }
    },
    clearInput() {
      this.newTodoItem = "";
    }
  },
  components: {
    Modal: AlertModal
  }
}
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: black;
  vertical-align: middle;
}
.closeModalBtn {
  color: #42b983;
}
</style>
