<template>
  <v-app id="app">
    <p id="judul">Kanban Board</p>
    <p id="notice">Don't forget to drag and drop your task as you progress!</p>
    <p id="add" @click="formActive = true" class="button" v-if="!formActive">Add new task</p>
    <p id="add" @click="formActive = false" class="button" v-if="formActive">close</p>
    <AddForm v-if="formActive == true" class="animated fadeIn" :class="{'animated fadeOut' : !formActive}"></AddForm>
    <div id="kanban-bar">
      <kanban v-for="(kanban, index) in kanbans" :key="index" :kanban-name="kanban" />
    </div> 
  </v-app>
</template>

<script>
import Kanban from '@/components/Kanban.vue'
import AddForm from '@/components/AddForm.vue'
export default {
  name: 'app',
  data() {
    return {
      kanbans: ['Plan', 'In-Progress', 'Done', 'Routine'],
      formActive: false
    }
  },
  components: {
    kanban: Kanban,
    AddForm
  },
  created() {

  },
  methods : {
    newTask() {

    },
    closeForm() {
      console.log('masuk tes woiii')
      this.formActive = false
    }
  }
}
</script>

<style>
p {
  margin: 0;
  
}
#notice {
  text-align: center;
  color: red;
}
#add {
  font-size: 20px;
  color: white;
  padding: 10px 15px;
  border-radius: 15px;
  background-color: #2C3E50;
  margin: 10px auto;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
#add:hover{
  cursor: pointer;		
  /* margin-top: 12px; */
}
#judul {
  width: 100%;
  color: #2C3E50;
  background-color: rgb(233, 233, 176);
  padding: 10px;
  font-size: 24px;
  margin-bottom: 0px;
  margin-left: auto;
  margin-right: auto;
}
body, html {
  width: 100%;
  height: 100%;
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
}

#kanban-bar {
  width: 100%;
  display: flex;
  justify-content: space-evenly;
  margin-bottom: 150px;
}
#navbar {
  width: 100%;
  height: 70px;
  padding: 10px;
  background-color: #2c3e50;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
</style>
