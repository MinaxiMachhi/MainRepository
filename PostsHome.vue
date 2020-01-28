<template>
  <div id="trainee-table">
    <div v-if="!addpost">
      <button class="glyphicon glyphicon-trash" @click="addpost='true'">Add Post</button>
      <table border="5px" class="table table-striped table-hover">
        <thead>
          <tr>
            <th>userId</th>
            <th>Title</th>
            <th>Body</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tr v-for="(post,index) in posts" :key="post._id">
          <td>{{post.userId}}</td>
          <td>{{post.title}}</td>
          <td>{{post.body}}</td>
          <td>
            <button class="glyphicon glyphicon-trash" @click="addpost='true'">Edit</button>
            <button class="glyphicon glyphicon-trash" @click="deleteData(index,post._id)">Delete</button>
          </td>
        </tr>
      </table>
    </div>
    <div v-else>
      <PostAdd :post="post" :addpost="addpost" @get="get($event)"></PostAdd>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import PostAdd from "@/components/PostAdd.vue";
// const url="localhost:3030";
export default {
  data() {
    return {
      posts: null,
      addpost: false
    };
  },
  async created() {
    this.posts = await this.getPosts();
    console.log(this.posts);
  },
  components: {
    PostAdd
  },

  methods: {
    async getPosts() {
      return (await axios.get("http://localhost:3030/posts/")).data.data;
    },
    get() {
      this.addpost = false;
    },
    deleteData(index, key) {
      axios
        .delete("http://localhost:3030/posts/" + key)
        .then(response => console.log(this.posts.splice(index, 1)));
    }
  }
};
</script>
<style scoped>
#app {
  color: #566787;
  font-family: "Varela Round", sans-serif;
  font-size: 13px;
}
.table-wrapper {
  background: #fff;
  padding: 20px 25px;
  margin: 25px 0;
  border-radius: 3px;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
.table-title {
  padding-bottom: 15px;
  background: #435d7d;
  color: #fff;
  padding: 16px 30px;
  margin: -20px -25px 10px;
  border-radius: 3px 3px 0 0;
}
.table-title h2 {
  margin: 5px 0 0;
  font-size: 24px;
}
.table-title .btn-group {
  float: right;
}
table.table tr th,
table.table tr td {
  border-color: #e9e9e9;
  padding: 12px 15px;
  vertical-align: middle;
}
table td a {
  font-weight: bold;
  color: #566787;
  display: inline-block;
  text-decoration: none;
  outline: none !important;
}
</style>
</style>
