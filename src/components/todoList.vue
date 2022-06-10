<template>
  <div id="todolist-demo">
    <h1>{{ title }}</h1>
    <div class="wrapper">
      <div class="userInput">
        <span>
          <input v-model="newTodoItem" placeholder="请输入你准备做的事情" />
          <button @click="handleAdd">添加</button>
        </span>
        <div class="userList">
          <ul>
            <li v-for="(item, index) in dolist" v-bind:key="item">
              {{ item }}
              <button @click="() => handleRemove(item, index)">删除</button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "It is a Todo List Demo!",
      newTodoItem: "",
      dolist: ["吃饭"],
    };
  },
  methods: {
    handleAdd() {
      if (this.newTodoItem === "") {
        alert("请输入正确的值");
      } else {
        this.dolist.push(this.newTodoItem);
      }
    },
    handleRemove(item, index) {
      this.dolist = [
        ...this.dolist.slice(0, index),
        ...this.dolist.slice(index + 1),
      ];
    },
  },
};
</script>

<style scoped>
#todolist-demo {
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 1px solid black;
  border-radius: 20px;
  height: 200px;
}

.wrapper {
  border: 1px solid pink;
  width: 50%;
  height: 50%;
  overflow: auto;
}
</style>