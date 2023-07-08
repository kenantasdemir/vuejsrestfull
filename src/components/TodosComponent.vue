<template>
    <div class="container mt-5">
        <div class="row">
            <div v-for="todo in todoList" :key="todo.id" class="col-md-4">
                <div class="card mb-4">
                    <div class="card-header">
                        <p class="card-title">Görev ID bilgisi: {{ todo.id }}</p>
                        <p class="card-subtitle">Bu görevden sorumlu kullanıcı: {{ todo.userId }}</p>
                    </div>
                    <div class="card-body">
                        <p class="card-text">{{ todo.title }}</p>
                    </div>
                    <div class="card-footer">
                        <p class="text-center" v-if="todo.completed">Tamamlandı <span class="text-success">&check;</span>
                        </p>
                        <p class="text-center" v-else>Tamamlanmadı <span class="text-danger">&times;</span></p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
  


<script>

import axios from "axios"

export default {
    data() {
        return {
            todoList: []
        }
    },
    created() {
        axios.get("https://jsonplaceholder.typicode.com/todos")
            .then(response => {
                // console.log(response.data)
                this.todoList = response.data
                console.log(this.todoList)
            }).catch(e => {
                console.log(e)
            })
    }

}


</script>