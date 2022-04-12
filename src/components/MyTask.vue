<template>
    <div class="card-body shadow mb-3">
        <input type="text" class="card-title form-control shadow-sm" placeholder="Taskname" v-bind:value="task.title">
        <div class="card-subtitle my-3">Section Name: {{ task.sectionName }}</div>
        <textarea type="text" class="card-text form-control my-3" v-bind:value="task.description"></textarea>
        <div class="d-flex justify-content-end">
        <button><font-awesome-icon icon="fa-solid fa-note-sticky" /></button>
        <button><font-awesome-icon icon="fa-solid fa-check" /></button>
        <button v-on:click="like()" v-bind:class="{yellow: isLiked}"><font-awesome-icon icon="fa-solid fa-star" /></button>
        <button v-on:click="del"><font-awesome-icon icon="fa-solid fa-trash" /></button>
        </div>
    </div>
</template>

<script>
export default ({
    name: "MyTask",
    data() {
        return {
            isLiked: false
        }
    },
    // 親コンポーネント"TaskSection"からobject型でtaskをもらう
    props: ['task'],
    // created: function(){
    //     console.log("test");
    //     console.log(this.task.sectionName);
    //     console.log(this.task);
    // },
    methods: {
        like: function(){
            this.isLiked = !this.isLiked;
        },
        del: function(){
            // console.log("emit直前のtaskId: " + this.task.id);
            return this.$emit("delete", this.task.id);
        }
    }
})
</script>

<style scoped>
    .yellow { color: #FFCC33 };
</style>
