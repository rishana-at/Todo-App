<template>
  <div class="card">
    <div class="container">
      <div class="center-items">
    <h1> To do List</h1>
 
  <input v-model="newtodo" class="input-todo" type="text" placeholder="What you want to do" @keyup.enter="addtodo">
   <button type="submit" v-on:click="addtodo" style="height:30px;
    margin-left: 1rem;">Add</button>
   <div class="continer">
      <div style="    margin-top: 1rem;
                     margin-bottom: -0.5rem;
                     margin-left: -1rem;">
        <a :class="{active:filter=='all'}" @click="filter='all'" class="atag">All </a>
        <a :class="{active:filter=='active'}" @click="filter='active'" class="atag">Pending</a>
        <a :class="{active:filter=='completed'}" @click="filter='completed'" class="atag">Completed</a>
       
      </div>
    </div>
   <hr>
   <!-- <table>
  <tr>
    <th>Todo item</th>
    <th>Actions</th>
   
  </tr>
  <tr>
    <td :key="todo.id" v-for="(todo ) in todosfiltered" style="display: flex;" >
      <input type="checkbox" v-model="todo.completed">
    <div v-if="!todo.editing" :class="{completed:todo.completed}"> {{ todo.title }}</div>
    
    <input v-else type="text" v-model="todo.title" @keyup.enter="doneEdit(todo)" v-focus></td>
    <td>   
      
   </td>

    
     </tr>
</table> -->
   
<div :key="todo.id" v-for="(todo,index ) in todosfiltered" style="display: flex; align-items: center; margin-top: 1rem;">
  <input type="checkbox" v-model="todo.completed" >
  <div v-if="!todo.editing" :class="{completed:todo.completed}" style="margin-right: 1rem; min-width: 10rem; display: flex; align-items: center;" >
    {{ todo.title }}
  </div>
  <input v-else type="text" v-model="todo.title" @keyup.enter="doneEdit(todo)" v-focus>
  <div style="display: flex; justify-content: flex-end; align-items: center; width: 10rem;">
    <button  @click="editTodo(todo)" v-if="!todo.editing" class="button-add">edit</button>
    <button @click.prevent="update" v-if="todo.editing" @click="doneEdit(todo)" class="button-add" >Update</button>
    <button style="align-items: center;" @click="removeTodo(index)">
      &times;
    </button>
  </div>
</div>
     <hr>
   
     <div class="remaining">
      {{ remaining }} items left
     </div>
    <div class="continer">
      <!-- <div >
        <button :class="{active:filter=='all'}" @click="filter='all'">All </button>
        <button :class="{active:filter=='active'}" @click="filter='active'">Pending</button>
        <button :class="{active:filter=='completed'}" @click="filter='completed'">Completed</button>
       
      </div> -->
      <div style="display: flex; justify-content: flex-end;">
        <button  v-if="showclearcompleted" @click="clearCompleted()">clear completed</button>
      </div>
    </div>
    
  </div>
    </div>
  </div>
  
</template>
<script>
 export default {
  name: 'TodoApp',
  data (){
  return{
  newtodo:'',
  idfortodo:3,
  filter:'all',
  todos:[{
    id:"1",
    title:'finish vue project',
    completed:false,
    editing:false
  },
  {
    id:"2",
    title:' Update yourself',
    completed:false,
    editing:false
  },
],

  }
 },
 directives: {
  focus: {
    // directive definition
    inserted: function (el) {
      el.focus()
    }
  }
},
computed:{
  remaining(){
    return this.todos.filter(todo=>!todo.completed).length
  },
  todosfiltered(){
    if(this.filter=='all'){
      return this.todos
    } else if(this.filter == 'active'){
      return this.todos.filter(todo => !todo.completed)
    } else if(this.filter == 'completed'){
      return this.todos.filter(todo => todo.completed)
    }
    return this.todos
  },
  showclearcompleted(){
    return this.todos.filter(todo=>todo.completed).length>0
  }

},
 methods:{
  addtodo(){
    
     
  if(this.newtodo.trim().length==0)
  {return}
  console.log('haai ')
    this.todos.push({
      id:this.idfortodo,
      title:this.newtodo,
      completed:false,
      editing:false
    })
    this.newtodo=' ',
    this.idfortodo++
  },
  editTodo(todo){
    todo.editing=true
  },
  doneEdit(todo){
        
  if(todo.title.trim().length==0)
  {return}
  
    todo.editing=false
  },
  removeTodo(index){
    this.todos.splice(index,1)
  },
  clearCompleted(){
    this.todos=this.todos.filter(todo=>!todo.completed)
  }
}
}




</script>

<style>
/* .center-items{
 align-items: center;
 
padding-top: 3rem;
padding-left: 30rem;
padding-right: auto;
} */
.input-todo{
  width: 50%;
  height: 25px;
}

.remaining{
  /* padding-left: 9rem; */
  display: flex;
   justify-content: flex-start;
   font-size: 12px;
}
.input{
  padding-left: 48rem;
}

table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}
.card {
  box-shadow: 3px 4px 8px 0 rgba(0,0,0,0.2);
    transition: 0.3s;
    width: 35%;
    background-color: #ffff;
    padding-top: 1rem;
    margin-left: 25rem;
    align-items: center;
    padding-left: 3rem;
    display: flex;
    margin-top: 5rem;
    background-color: lightblue;

}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}

/* .container {
  padding: 2px 16px;
} */
.atag:hover{
  cursor: pointer;
  
}
.atag{
  font-size: 0.9rem;
    padding-top: 111rem;
    margin-top: 5rem;
    margin-bottom: 5rem;
  margin-left: 1rem;
}

</style>