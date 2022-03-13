<template>
    <!-- <h5>{{ this.count }}</h5>
    <button @click="addCount">tambah</button>

    <h4>{{ valueInput }}</h4>
    <input type="input" v-model="valueInput" />
    <h4>{{ this.status }}</h4>
    <div v-if="status">status bernilai true</div>
    <div v-else>status bernilai false</div>
    <button @click="changeStatus">ubah status</button>

    <div v-for="(data, index) in datas" :key="index">{{ data }}</div> -->

    <h4>Todo List</h4>
    <h6>{{ this.angkaAcak() }}</h6>
    <h6>{{ checkValueInput }}</h6>
    <input v-model="valueInput" v-on:keyup.enter="addTodos" />
    <button @click="addTodos">Tambah</button>
    <Activities :todos="todos" @deleteTodo="deleteTodo" />

    <div>Total todo: {{ this.totalTodo }}</div>
    <div>Belum selesai: {{ this.undoneTodo }}</div>
    <div>Sudah selesai: {{ this.doneTodo }}</div>
</template>

<script>
import Activities from "./components/Activities.vue";

export default {
    name: "App",
    components: {
        Activities,
    },
    data() {
        return {
            count: 0,
            valueInput: "",
            status: true,
            datas: ["ilham", "kukuh", "prakosa", "tees"],
            todos: [],
        };
    },
    computed: {
        totalTodo() {
            return this.todos.length;
        },
        doneTodo() {
            return this.todos.filter((todo) => todo.isDone).length;
        },
        undoneTodo() {
            return this.todos.filter((todo) => !todo.isDone).length;
        },
        checkValueInput() {
            return this.angka1 + this.angka2;
        },
    },
    methods: {
        addCount() {
            this.count++;
        },
        changeStatus() {
            this.status = !this.status;
        },
        addTodos() {
            this.todos.push({
                activity: this.valueInput,
                isDone: false,
            });
            this.valueInput = "";
        },
        deleteTodo(todoIndex) {
            this.todos.splice(todoIndex, 1);
        },
        angkaAcak() {
            return Math.random();
        },
    },
    watch: {
        valueInput(newVal) {
            if (newVal) {
                this.angkaAcak();
            }
        },
    },
};
</script>

<style>
#app {
    /* font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px; */
}
</style>
