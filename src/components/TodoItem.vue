<template>
        <div class="todo" v-bind:class="{completed: todo.completed}">
                <div class="todo-body">
                        <input type="checkbox" 
                                v-bind:checked="todo.completed ? 'checked': '' "
                                v-on:change="checkTodo"
                        >
                        {{todo.title}}
                </div>

                <div class="todo-actions">
                        <button @click="$emit('delete-todo', todo.id)">Eliminar</button>
                </div>
        </div>
</template>

<script>
        export default {
                name: 'TodoItem',
                props: ['todo'],
                methods: {
                        checkTodo(){
                                this.todo.completed = !this.todo.completed;
                        }
                }
        }
</script>

<style scoped>
        .todo{
                border-bottom: 1px solid #ccc;
                padding: 10px;
        }

        .todo:not(.completed):hover{
                background: #eee;
        }

        .completed{
                color: #ccc;
                text-decoration: line-through;
        }

        .completed .todo-body{
                text-decoration: line-through;
        }

        .todo-body, .todo-actions{
                display: inline-block;
                vertical-align: top;
        }

        .todo-body{
                width: 85%;
        }

        .todo-actions{
                padding: 0 10px;
                width: 10%;
        }

        button{
                border: none;
                border-radius: 3px;
                padding: 10px;
                background: #ccc;
        }

        button:hover{
                background: brown;
                color: white;
        }
</style>