<template>
    <div>
        <h1>Minha lista de tarefa</h1>
        <button @click="() => showList = !showList">ver a lista</button><br>
        <input type="text" v-focus />
        <ul v-if="showList">
            <li v-for="(task, index) of tasks" 
                :key="`${task}_${index}`">
                {{task.title}}
            </li>
        </ul>
        <div v-else>
            Lista Escondida
        </div>
    </div>
</template>

<script>
const focus = {
    inserted: (element) => {
        element.focus()
    }
}
export default {
    directives: {
        focus
    },
    data: () => ({
        showList: false,
        tasks: [
            {title: "Fazer o curso", isDone: false},
            {title: "Fazer o commit", isDone: false},
            {title: "Fazer o deploy", isDone: false},
        ]
    }),
}
</script>

<style>

</style>