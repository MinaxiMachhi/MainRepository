<template>
  <div>
    <div id="add" style="display:block">
      Title
      <input v-model="title" />
      <br />Body
      <input v-model="body" />
      <button @click="PostData()">Post Data</button>
      <button @click="PostData()">Edit Data</button>
    </div>
  </div>
</template>
<script>
import axios from "axios";
const url = "http://localhost:3030/posts/";
export default {
  props: ["post", "addpost"],
  data() {
    return {
      id: 1,
      title: "",
      body: ""
    };
  },
  methods: {
    PostData() {
      document.getElementById("add").style.display = "none";
      axios
        .post(url, {
          userId: 1,
          title: this.title,
          body: this.body
        })
        .then(res => console.log((this.post = res.data.data)));
      this.$emit("get", this.addpost);
    }
  }
};
</script>