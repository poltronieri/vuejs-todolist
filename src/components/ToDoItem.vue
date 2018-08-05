<template>
    <li class="list-group-item">
        {{todo.text}}
        <button @click="removeItem(todo)" type="button" class="btn btn-outline-danger btn-sm float-right">
            <i class="far fa-trash-alt"/>
        </button>
    </li>
</template>

<script>
export default {
    name:'to-do-item',
    props:['todo'],
    methods:{
        removeItem(todo){
            this.$emit('delete', todo);
        }
    }

}
</script>

<style>
</style>
