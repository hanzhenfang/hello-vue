<template>
  <div>
    <h1>
      请输入你的问题:
      <input v-model="question" />
    </h1>
    <p :class="isActive ? 'active' : ''">问题的回答是:{{ answer }}</p>
    <button @click="changeColor">切换字体颜色</button>
    <p>上一个问题是：{{ oldQuestion }}</p>
    <h2 v-if="isActive">现在isActive有值</h2>
    <h3 v-else>现在没有值</h3>

    <ul>
      <li
        v-for="(item, index) in todos"
        v-bind:key="index"
        :class="index % 2 == 0 ? 'oddNumber' : 'evenNumber'"
      >
        {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      message: "hello word",
      login: false,
      todos: [
        { id: 0, name: "锂", sex: "男" },
        { id: 1, name: "钠", sex: "男" },
        { id: 2, name: "氪", sex: "男" },
        { id: 3, name: "锶", sex: "男" },
      ],
      myList: {
        age: 18,
        friends: "郭奇",
      },
      question: "如:今年多少岁了?",
      answer: "Questions usually contain a question mark. ;-)",
      oldQuestion: "",
      isActive: true,
    };
  },
  watch: {
    question(_, oldQuestion) {
      console.log(oldQuestion);
      this.oldQuestion = oldQuestion;
    },
    login(val) {
      console.log(val);
    },
  },
  methods: {
    changeColor() {
      console.log(this.isActive);
      this.isActive = !this.isActive;
    },
    handleReverse() {
      this.message = this.message.split(" ").reverse().join(" ");
    },
    handleLogin() {
      this.login = !this.login;
    },
    doSomething() {
      console.log(this);
    },
    getAnswer() {
      this.answer = "thinking";
      axios
        .get("https://yesno.wtf/api")
        .then((response) => {
          console.log(response);
          this.answer = response.data.answer;
        })
        .catch((erro) => {
          console.log(erro);
        });
    },
  },
  computed: {
    reverseMessage() {
      return this.message.split(" ").reverse().join(" ");
    },
  },
  mounted() {
    console.log("已挂载");
    this.getAnswer();
  },
};
</script>

<style scoped>
.active {
  color: red;
  font-size: 2rem;
}
.oddNumber {
  background-color: bisque;
}
.evenNumber {
  background-color: blue;
}
</style>

