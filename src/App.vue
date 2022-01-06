<template>
  <div id="app">
    <task
      v-for="(task, index) in tasks"
      :message="task.message"
      :key="index"
      :position="task.position"
      :index="index"
      :ref="'task' + index"
    />
  </div>
</template>

<script>
import Task from "./components/Task.vue";
//import LeaderLine from "leader-line-vue";

export default {
  name: "App",
  components: { Task },
  data() {
    return {
      tasks: [
        { message: "hello", position: { left: 10, top: 4 } },
        { message: "hello", position: { left: 30, top: 33 } },
        { message: "hello", position: { left: 50, top: 12 } },
      ],
    };
  },
  mounted() {},
  watch: {
    tasks: function (val) {
      // new LeaderLine(
      //   document.querySelector("#task-0"),
      //   document.querySelector("#task-1")
      // )
      //     new LeaderLine(
      //   document.querySelector("#task-1"),
      //   document.querySelector("#task-2")
      // );
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: grey;
  height: 100vh;
  width: 100vw;
  display: flex;
}
</style>
