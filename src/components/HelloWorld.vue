<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{ subtitle }}</h2>
    <button v-on:click="showAlert">click if you dare</button>
    <p>{{ itemsTitle }}</p>
    <ul>
      <li v-for="item in dataList" v-bind:key="item">{{ item.value }}</li>
    </ul>

    <button @click="changeData('mutated data')">change data</button>
    <p>{{ someInternalData.data }}</p>

    <input v-model="message" placeholder="edit me" />
    <p>Message is: {{ message }}</p>
    <NewComponent />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import NewComponent from "@/components/NewComponent.vue";

export default defineComponent({
  name: "HelloWorld",
  props: {
    msg: String,
    subtitle: String,
    dataList: Array,
  },
  data() {
    return {
      someInternalData: { data: "internal component data" },
      message: "",
    };
  },
  methods: {
    showAlert() {
      alert("a usuless alert");
    },
    changeData(newData: string) {
      this.someInternalData = { data: newData };
    },
  },
  computed: {
    itemsTitle() {
      return "items:";
    },
  },
  components: {
    NewComponent,
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
