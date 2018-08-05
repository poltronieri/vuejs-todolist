<template>
		<div class="container-fluid">
      <h2 class="title text-center p-3">
        Awesome <strong class="color-1">Vue</strong><strong class="color-2">JS</strong> ToDo List!
      </h2>
      <div class="input-group mb-3">
        <input type="text" class="form-control" placeholder="type a todo here and press enter to add (or click in the button)" v-model="todo" v-on:keyup.enter="addItem" />
        <div class="input-group-append">
          <button v-on:click="addItem" class="btn btn-success" type="button" id="button-addon2">+</button>
        </div>
      </div>
      <ul class="list-group">
				<ToDoItem v-for="todo in list" :todo="todo" :key="todo.id" @delete="onDeleteItem"/>
      </ul>
		</div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue';
import { v4 } from 'uuid';
export default {
name: 'to-do',
	components: {
		ToDoItem
	},
	data() {
			return {
					list: [],
					todo: '',
			}
	},
	methods: {
			addItem(){
					if(this.todo){
						this.list.push({id:v4(), text:this.todo});
						this.todo='';
					} else {
						alert('preencha o campo!');
					}

			},
			onDeleteItem(todo){
        this.list = this.list.filter(item => item !== todo);
      } 
	}
}
</script>

<style>
body {
  color: gray;
  background-color: #f7f7f7;
}
.color-1 {
  color: #35495e;
}

.color-2 {
  color: #41b883;
}
</style>
