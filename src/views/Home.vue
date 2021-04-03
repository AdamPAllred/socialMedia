<template>
  <div>
    <h1> Welcome to NewSocial!!! </h1>
    <p class="header"> Here at NewSocial we are devotated to keeping your data save and making connections possible! </p>
    <p class="header"> Use the serach bar to search someone's username or use a "#", to look up a specific hashtag! </p>
    <p class="header"> No comments on post, so no hate! Only hearts to give to people! </p>
    <div class="wrapper">
      <div class="search">
        <form class="pure-form">
          <i class="fas fa-search"></i><input v-model="searchText" />
        </form>
      </div>
    </div>
    <PostList :posts="posts" />
    <p><a href="https://github.com/AdamPAllred/socialMedia">GitHub Link!</a></p>
  </div>
</template>

<script>
import PostList from "../components/PostList.vue"
export default {
  name: 'Home',
  components: {
    PostList,
  },
  data() {
    return {
    	searchText: '',
    }
  },
  computed: {
    posts() {
      var newPosts = [];
      var currString = this.searchText.toString();
      if(currString == "#") {
        newPosts = [];
        return this.$root.$data.posts;
      }
      else {
        if(currString.charAt(0) == '#') {
          for(var i = 0; i < this.$root.$data.posts.length; i++) {
            for(var j = 0; j < this.$root.$data.posts[i].tags.length; j++) {
              if(this.$root.$data.posts[i].tags[j].toLowerCase().search(currString.substring(1).toLowerCase()) >= 0) {
                if(newPosts.length == 0) {
                  newPosts.push(this.$root.$data.posts[i]);
                  break;
                }
                else if(!newPosts.includes(this.$root.$data.posts[i])) {
                  newPosts.push(this.$root.$data.posts[i]);
                  break;
                }
              }
            }
          }
          console.log(newPosts.length);
          return newPosts;
        }
      }
      return this.$root.$data.posts.filter(post => post.userName.toLowerCase().search(this.searchText.toLowerCase()) >= 0);
    }
  },
}
</script>

<style scoped>

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

.search {
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 50%;
  align: center;
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
