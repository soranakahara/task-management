<template>
    <div class="card p-4 shadow mx-3">
        <div class="input-group mb-3 shadow-sm">
          <input type="text" class="form-control" v-model="sectionName" v-on:change="changed()" placeholder="Section Name">
        </div>
        <!-- task -->
        <div v-for="(mytask, index) in taskList" :key="index">
            <my-task v-bind:task="mytask" v-on:delete="deleteTask" ></my-task>
        </div>
        <!-- add button -->
        <button v-on:click="createTask()" class="d-flex align-self-start"><font-awesome-icon icon="fa-solid fa-plus" /></button>
    </div>
</template>

<script>
import MyTask from './MyTask.vue'
// import TaskNew from './components/TaskNew.vue'

export default ({
    name: "TaskSection",
    data() {
        return {
            sectionName: "",
            taskList: [],
            newTaskId: 0,
            
        }
    },
    components: {
        MyTask,
    },
    props: ['newId'], // sectionを新規作成するときのId
    created: function(){
        this.createTask();
    },
    methods: {
        createTask: function(){
            // console.log("cerateTask"+this.sectionName);
            const newTask = {
                id: this.newTaskId,
                sectionId: this.newId,
                sectionName: this.sectionName,
                title: "",
                description: "",
            };
            // console.log(newTask.sectionName);
            this.taskList.push(newTask);
            this.newTaskId += 1;
        },
        changed: function(){
            for (let i=0; i<this.taskList.length; i++){
                this.taskList[i].sectionName = this.sectionName;
            }
        },
        deleteTask(taskId){
            this.taskList = this.taskList.filter((task) => {
                return (task.id !== taskId);
            });
        }
    }
})
</script>
