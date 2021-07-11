<template>
  <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder': '', 'task']">
  <h3>{{task.text}} <i @click="$emit('delete-task',task.id)" class="fas fa-trash-alt"></i></h3>    
  <p>{{task.day}}</p>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    task: Object
  }
}
</script>


<style scoped>
  .fas:hover {
    color: rgb(139, 54, 39);
  }
  .fas {
    color: tomato;
    z-index: 10;
    transition: all .2s;
  }
  .fas:active {
    color: black;
  }
  .task {
    background: aliceblue;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
    position: relative;
    transition: all .5s;
    overflow: hidden;
  }

  .task:before {
    content: '';
    position: absolute;
    left: -100%;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(165, 170, 175, 0.185);
    transition: all .5s;
  }

  .task:hover:before {
    left:0;
  }

  .task.reminder {
    border-left: 5px solid Chartreuse;
    transition: all .1s;
  }

  .task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
</style>