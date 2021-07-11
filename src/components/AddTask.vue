<template>
  <form @submit="onSubmit" class="add-form" ref="form">
    <div class="form-control">
      <label for="">Task</label>
      <input type="text" v-model="text" name="text" placeholder="task goes here" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input type="text" v-model="day" name="day" placeholder="Day&Time"/>
    </div>
    <div class="form-control fc-checkbox">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

  <a href="#" v-on:click="onSubmit" class='button-submit'> Submit </a>
  </form>
</template>

<script>
  export default {
    name: 'AddTask',
    data() {
      return {
        text: '',
        day: '',
        reminder: false
      }
    },
    methods: {
      onSubmit(e) {
        e.preventDefault()
        if(!this.text) {
          alert('Please add a task')
          return
        }
        const newTask = {
          id: Math.floor(Math.random() * 10000),
          text: this.text,
          day: this.day,
          reminder: this.reminder
        }

        this.$emit('add-task', newTask)  
        this.text = ''
        this.day = ''
        this.reminder = false
      }
    }
  }
</script>

<style scoped>
  .add-form {
    display: grid;
    margin: 4em 0;
  }
  .form-control {
    display: grid;
    margin: 1em 0;
  }
 
  .form-control label {
     text-align: left;
     margin: .5rem 0;
  }

  input {
    padding: 1em;
  }
  .fc-checkbox {
    display: flex;
    align-items: center;
  }
  .fc-checkbox label {
    margin-right: 1em;
  }
  .fc-checkbox input {
    display: block;
    width: 1.5rem;
    height: 1.5rem;
  }
  .button-submit { 
    width: 150px;
    text-align: center;
    text-decoration: none;
    font-size: 20px;
    color: tomato;
    padding: 10px 20px;
    background: transparent;
    position: relative;
    overflow: hidden;
    transition: all .5s;
  }
  .button-submit:active  {
     background: rgb(247, 69, 37);
  }
  .button-submit:before {
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    bottom: 90%;
    left: 0;
    background-color: tomato;
    z-index: -1;
    transition: all .5s;

  }
  .button-submit:hover:before {
    bottom: 0;
  }

  .button-submit:hover {
    color: white;
  }

</style>