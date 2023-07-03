<template>
  
  <div class="container">
    <div> 
       <h1>TO DO LIST</h1>
    </div>
    <div class="form-group mx-5">
       
       <input type="text" class="form-control" placeholder="Enter the task" v-model="task" required><br><br>
   </div>
   <div class="mx-5">
   <input type="submit" value="ADD TASK" @click="addtask"> 
  </div>
       <div class="container text-center">
           <div class="row mt-5 ">
              <div class="col card-body card" v-for="(todo, index) in todos" :key="index" style="background-color: rgb(156, 187, 255) ; border: black 1px solid; width: 18rem; margin:1%">
                  <h5 class="card-title">{{ todo.title }}</h5>
                  <p class="card-text">{{ todo.date }}</p>
                  <button @click="deleteCard(index)" style="background-color: rgb(254, 185, 185);border: 0; border-bottom: 5%;">Delete</button>
                </div>
              </div>   
           </div>
         </div>



</template>

<script>
export default{
  name: 'App',
  data: ()=>({
    task:'',
    todos: [
        { title: 'Your ToDo Will Appear here', date: 'ToDo Created date will appear here' }
      ]
  }),
  methods:{
    addtask() {
      if (this.task.length > 0) {
        const currentdate = new Date();
        const datatoadd = {
          title: this.task,
          date: currentdate
        };
        this.todos.unshift(datatoadd);
        this.task = '';
      } 
      else {
        alert('Please Enter Your TODO!');
      }
    },
    deleteCard(index) {
      if (confirm('Are you sure?')) {
        this.todos.splice(index, 1);
      }
    }
  }
}
  

  </script>

<style>
h1{
text-align: center;
padding-top: 50px;
color: black;
}

#task{
    text-align: center;
}


body{
    background-color: bisque;
}


</style>
