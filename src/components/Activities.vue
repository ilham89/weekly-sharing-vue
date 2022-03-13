<template>
    <div class="hello">
        <ol>
            <li v-for="(todo, index) in todos" :key="index">
                <div class="todo">
                    <div v-if="!todo.isDone">
                        {{ todo.activity }}
                    </div>
                    <s v-else>{{ todo.activity }}</s>

                    <input type="checkbox" v-model="todo.isDone" />
                    <button @click="deleteTodo(index)">Hapus</button>
                </div>
            </li>
        </ol>
    </div>
</template>

<script>
export default {
    name: "Activities",
    props: {
        todos: {
            type: Array,
            default: () => [],
        },
    },
    methods: {
        deleteTodo(index) {
            this.$emit("deleteTodo", index);
        },
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todo {
    display: flex;
}
</style>
