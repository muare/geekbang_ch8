<template>
    <div id="app">
      <input v-model="message">
      <input :value="message" @input="handleChange">
        {{message}} {{message+message}}
        <div :id="message"></div>
        <!-- <ul>
            <todo-item v-for="item in list" :title="item.title" :del="item.del"></todo-item>
        </ul> -->
        <todo-list>
            <todo-item @delete="handleDelete" v-for="item in list" :title="item.title" :del="item.del" :key="item.title">                                
                <template v-slot:pre-icon="{value}">
                    <span >PREICON {{value}}</span>               
                </template>
                <template v-slot:post-icon>
                    <span >POSTICON</span>
                </template>
            </todo-item>
        </todo-list>
    </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
import TodoItem from "./components/TodoItem.vue";

export default {
  name: "App",
  components: {
    TodoList,
    TodoItem
  },
  data() {
    return {
      message: "hello world",
      list: [
        {
          title: "course 1",
          del: false,
        },
        {
          title: "course 2",
          del: true,
        },
      ],
    };
  },
  methods: {
    handleChange(e) {
      this.message = e.target.value
    },
    handleDelete(val) {
      console.log("handle delete", val);
    },
  },
};
</script>

