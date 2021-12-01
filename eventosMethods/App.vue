<template>
    <div>
        <h1>Minha lista de tarefa</h1>
        <button @click="handleShowHideList">ver a lista</button><br>
        <input type="text" 
        v-focus 
        v-model="currentTask" 
        @keyup.enter="addTask"
        />
        <ul v-if="showList">
            <li v-for="(task, index) of tasks" 
                :class="task.isDone ? 'line-through' : null"
                :key="`${task}_${index}`"
                class="task-item"
                @dblclick="complete(task)">
                {{task.title}}
                <button @click="remove(task)">&times;</button>
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
        currentTask: '',
        showList: false,
        tasks: [
            {title: "Fazer o curso", isDone: false},
            {title: "Fazer o commit", isDone: false},
            {title: "Fazer o deploy", isDone: false},
        ]
    }),
    methods: {
        addTask(){
            console.log("O que tem na v-model", this.currentTask);
            this.tasks.push({title: this.currentTask, isDone: false})
            this.currentTask = ''
        },
        handleShowHideList(){
            this.showList = !this.showList
        },
        remove(task){
            console.log(task);
            this.tasks = this.tasks.filter(item => item.title != task.title)
        },
        complete(task){
            console.log(task);
            this.tasks = this.tasks.map(item =>{ 
                if(item.title === task.title) item.isDone = !item.isDone
                return item
            })
            console.log("current tasks");
            console.log(this.tasks);
        }
    },
}
</script>

<style scoped>
    .line-through{
        text-decoration: line-through;
    }
    .task-item{
        cursor: pointer;
    }
</style>