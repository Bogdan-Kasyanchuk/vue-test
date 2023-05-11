<!-- <template>
  <h1>TEST VUE</h1>
  <div>
    <h2>Лічильник</h2>
    <p :class="{ p1: count === 5, p2: count === 10 }">{{ count }}</p>
    <button @click="add">+1</button>
    <button @click="remove">-1</button>
    <p class="p1" v-if="count === 5">Лічильник нарахував 5</p>
    <p class="p2" v-else-if="count === 10">Лічильник нарахував 10</p>
    <p v-else>Лічильник нарахував................</p>
  </div>
  <div class="line">-------------------- Розділювач --------------------</div>
  <div>
    <div>Хедер</div>
    <button :class="{ btnShow: show, btnNotShow: !show }" @click="setShow">
      Show
    </button>
    <div v-show="show">
      Боді
      <ul>
        <li>Bogdan</li>
        <li>Fedor</li>
        <li>Petro</li>
      </ul>
    </div>
  </div>
  <div class="line">-------------------- Розділювач --------------------</div>
  <div>
    <h2>Todos</h2>
    <form @submit.prevent>
      <input
        v-bind:value="title"
        @input="title = $event.target.value"
        type="text"
        placeholder="title"
      />
      <input
        v-bind:value="desc"
        @input="desc = $event.target.value"
        type="text"
        placeholder="desc"
      />
      <button class="btn" @click="createTodo">Add totdo</button>
    </form>
    <ul class="list-ul">
      <li class="item-li" v-for="item in todos" :key="item.id">
        <h3>{{ item.title }}</h3>
        <p :class="{ done: item.status }">{{ item.desc }}</p>
        <input type="checkbox" v-model="item.status" />
        <button class="btn" @click="deleteTodo(item.id)">Del</button>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      count: 0,
      show: false,
      todos: [
        {
          id: crypto.randomUUID(),
          title: "Покупка",
          desc: "Купити продукти",
          status: true,
        },
        {
          id: crypto.randomUUID(),
          title: "Робота",
          desc: "Зробити програму",
          status: false,
        },
      ],
      title: "",
      desc: "",
    };
  },

  methods: {
    add() {
      this.count += 1;
    },

    remove() {
      if (this.count <= 0) return;
      this.count -= 1;
    },

    setShow() {
      this.show = !this.show;
    },

    createTodo() {
      const newTodo = {
        id: crypto.randomUUID(),
        title: this.title,
        desc: this.desc,
        status: false,
      };

      this.todos.push(newTodo);
      this.title = "";
      this.desc = "";
    },

    deleteTodo(id) {
      this.todos = this.todos.filter((el) => el.id !== id);
    },
  },

  mounted() {
    console.log(`The initial count is ${this.count}.`);
  },

  updated() {
    // console.log(this.todos);
  },
};
</script>
<style>
.p1 {
  font-size: 20px;
  color: red;
}

.p2 {
  font-size: 20px;
  color: blue;
}

.line {
  font-size: 20px;
  font-weight: 900;
  color: rgb(83, 128, 0);
}

.btnShow {
  background-color: green;
}

.btnNotShow {
  background-color: red;
}

.done {
  color: red;
  text-decoration: line-through;
}

.list-ul {
  display: flex;
  list-style: none;
}

.item-li {
  border: 1px solid red;
  padding: 10px;
}

.item-li:not(:last-child) {
  margin-right: 20px;
}

.btn {
  margin-left: 20px;
}

button {
  cursor: pointer;
}
</style> -->

<!-- *********************************************** -->

<template>
  <vue-tel-input
    v-model="phone"
    mode="international"
    :dropdownOptions="{
      showDialCodeInList: true,
      showSearchBox: true,
      showFlags: true,
    }"
    :inputOptions="{
      showDialCode: true,
      autocomplete: 'off',
      placeholder: 'Enter a phone number',
      styleClasses: 'input',
    }"
    :validCharactersOnly="true"
    :styleClasses="'wrapper'"
  ></vue-tel-input>
</template>

<script>
import { ref } from "vue";
import { VueTelInput } from "vue-tel-input";
import "../node_modules/vue-tel-input/dist/vue-tel-input.css";

export default {
  components: {
    VueTelInput,
  },

  setup() {
    const phone = ref(null);

    return {
      phone,
    };
  },

  updated() {
    console.log(this.phone);
  },
};
</script>

<style>
.input {
  font-size: 30px;
  color: red;
}
.wrapper {
  height: 60px;
}
</style>
