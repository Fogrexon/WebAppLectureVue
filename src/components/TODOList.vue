<template>
    <div>
    <h1>TODO List</h1>
    <div>
        <label for>
            タスク名
            <input type="text" v-model="newItemName">
        </label>
        <button @click="addItem">add</button>
    </div>
    <h2>未完</h2>
    <div v-for="item in items">
        <div v-if="!item.isDestroyed&&!item.isDone" class="taskBox" :class="{done: item.isDone}">
            <div class="item">タスク名: {{ item.taskName }}</div>
            <button　v-if="item.isDone" class="Done" @click="item.isDone = false"> 取り消し </button>
            <button　v-else class="Done" @click="item.isDone = true"> 完了 </button>
            <button　@click="item.isDestroyed=true"> 削除 </button>
        </div>
    </div>
    <h2>完了済み</h2>
    <div v-for="item in items">
        <div v-if="!item.isDestroyed&&item.isDone" class="taskBox" :class="{done: item.isDone}">
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
    data() {
        return {
            items: [
            ],
            count:0,
            newItemName: ""
        }
    },
    methods: {
        addItem:function(){
            this.items.push({ taskName: this.newItemName, isDone: false, isDestroyed: false});
            this.count++;
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