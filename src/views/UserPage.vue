<template>
  <div>
    <h1> Beth123's Page</h1>
      <div class="info">
          <p> Welcome to my page! I love all cute things, dogs, cats, anything!, please give me a follow and have so much fun.
          I hope you have a blast and have a great day!
          Welcome to my page! I love all cute things, dogs, cats, anything!, please give me a follow and have so much fun.
          Welcome to my page! I love all cute things, dogs, cats, anything!, please give me a follow and have so much fun.  </p>
      </div>
    <PostList :posts="posts" />
  </div>
</template>

<script>
import PostList from "../components/PostList.vue"
export default {
  name: 'Home',
  components: {
    PostList
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
      console.log(addPost.length);
      return addPost;
    }
  },
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
