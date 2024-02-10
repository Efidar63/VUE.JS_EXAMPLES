<template>
    <form @submit.prevent="sendData">
        <input type="text" v-model="text"/>
        <p>{{ text }}</p>
        <select>
            <option>Vue</option>
            <option>React</option>
            <option>Svelte</option>
        </select>
        <p>{{framework}}</p>
    <hr>
    <input type="checkbox" id="checkbox1" v-model="checked">
    <label for="checkbox1">Onay</label>
    <p>Result: {{checked ? 'Agree' : 'Disagree'}}</p>
    <br>
    <div>
      <input type="checkbox" id="Vue" value="Vue" v-model="frameworks">
      <label for="Vue">Vue</label>
    </div>
    <div>
      <input type="checkbox" id="React" value="React" v-model="frameworks">
      <label for="React">React</label>
    </div>
    <div>
      <input type="checkbox" id="Svelte" value="Svelte" v-model="frameworks">
      <label for="Svelte">Svelte</label>
    </div>
    <p>Choosen Frameworks: {{frameworks}}</p>
    <hr>
    <h3>Students</h3>
    <input type="text" v-model="student" @keyup.alt="addStudent">
    <div v-for="student in students" :key="student">
      <span @click="deleteStudent(student)">{{student}}</span>
    </div>
    <br>
    <button>Send</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      text:'Write a Text',
      framework: 'Choose a Framework ',
      checked: false,
      frameworks: [],
      student: '',
      students: []
    }
  },
  methods: {
    addStudent(e) {
      if(e.key==',' && this.student) {
        if(!this.students.includes(this.student)){
          this.students.push(this.student)
        }
        this.student=''
      }
    },
    deleteStudent(student){
      this.students = this.students.filter(item => student !== item)
    },
    sendData(){
      console.log("Datas Send")
    }
  },
}
</script>

<style>

</style>>