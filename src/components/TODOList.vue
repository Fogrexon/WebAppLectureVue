<template>
    <div>
    <h1>TODO List</h1>
    <div>
        <label for>
            名前
            <input type="text" v-model="newItemName">
        </label>
        <button @click="addItem">add</button>
    </div>
    <div v-for="item in items" :key="item.taskName">
        <div v-if="!item.isDestroyed" class="taskBox" :class="{done: item.isDone}">
            <div class="item">タスク名: {{ item.taskName }}</div>
            <button　v-if="item.isDone" class="Done" @click="item.isDone = false"> 取り消し </button>
            <button　v-else class="Done" @click="item.isDone = true"> 完了 </button>
            <button　@click="item.isDestroyed=true"> 削除 </button>
        </div>
    </div>
    </div>
</template>

<script>
export default {
    name: "TODOList",
    newItemName: "",
    data() {
        return {
            items: [
                {taskName:"新聞読む", isDone: true, isDestroyed:false},
                {taskName:"謎", isDone: false, isDestroyed: false}
            ]
        }
    },
    methods: {
        addItem:function(){
            this.items.push({ taskName: this.newItemName, isDone: false, isDestroyed: false});
        },


    }
};

</script>

<style>
div .done{
    background-color: #ddd;
}

div not(.done){
    background-color: #fff;
}
</style>