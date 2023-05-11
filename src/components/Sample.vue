<!-- <template>
    <h3>{{ mssg }}</h3>
        <div>
          <h3>this is a sample component</h3>
        <h2>{{ name }}</h2>
        <h3>{{ count }}</h3>
        <input v-model="addnew" type="text" placeholder="enter todo" >
        <button @click="addtodo">add</button>
        <ol>
          <li v-for="frt in fruits" >
            {{ frt }}
          </li>
        </ol>
        </div>
    
</template>
<script>
export default{
    name:'Sample',
    data:function(){
      return{ count:45}
    },
    props:[fruits],
    method: function addtodo(){
      return this.fruits.push(addnew)
    }
  
}

</script> -->