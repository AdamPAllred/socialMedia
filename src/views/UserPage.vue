<template>
  <div>
    <h1> Beth123's Page</h1>
    <div class="info">
      <button @click="editPage()">Edit Page</button>
    </div>
      <div class="info">
          <div id="bio"></div>
      </div>
      <div v-if="this.editingPage">
        <div class="info">
          <input v-model="bio" placeholder="Bio">
          <button @click="editBio(bio)">Edit Bio</button>
        </div>
      </div>
    <PostList :posts="posts" />
  </div>
</template>

<script>
import PostList from "../components/PostList.vue"
export default {
  name: 'UserPage',
  components: {
    PostList
  },
  data() {
    return {
      editingPage: false,
      bio: null,
    }
  },
  computed: {
    posts() {
      var addPost = [];
      var currPosts = this.$root.$data.posts;
      for(var i = 0; i < currPosts.length; i++) {
        if(currPosts[i].userName == "Beth123") {
          addPost.push(currPosts[i]);
        }
      }
      return addPost;
    },
  },
  methods: {
    editBio(bio) {
      let results = "";
      results += "<p> Bio: ";
      results += bio;
      results += "</p>";

      document.getElementById("bio").innerHTML = results;
    },
    editPage() {
      if(this.editingPage) {
        this.editingPage = false;
      }
      else {
        this.editingPage = true;
      }
    },
  }
}
</script>

<style scoped>
.info {
  text-align: center;
  margin-right: 15%;
  margin-left: 15%;
  font-size:20px;
}


h1 {
  text-align: center;
  text-decoration: underline;
  margin-bottom: 30px;
}

p {
  text-align: center;
}

.header {
  font-size: 20px;
}


.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.search {
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 50%;
}

form {
  display: table;
  width: 100%;
}

i {
  display: table-cell;
  padding-left: 10px;
  width: 1px;
}

input {
  display: table-cell;
  font-size: 20px;
  border: none !important;
  box-shadow: none !important;
  width: 100%;
  height: 40px;
}
</style>
