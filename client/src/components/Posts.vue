<template>
  <div class="posts">
    <h1>MENU</h1>
    <div v-if="posts.length > 0" class="table-wrap">
      <div>
        <h1><router-link v-bind:to="{ name: 'NewPost' }" class="">Add Hot Dog</router-link></h1>
      </div>
      <table>
        <tr>
          <td width="600">Title</td>
          <td width="700">Description</td>
          <td width="400" align="center">Action</td>
        </tr>
        <tr v-bind:key="post.id" v-for="post in posts">
          <td>{{ post.title }}</td>
          <td>{{ post.description }}</td>
          <td align="center">
            <router-link v-bind:to="{ name: 'EditPost', params: { id: post._id } }">Edit</router-link> |
            <a href="#" @click="deletePost(post._id)">Delete</a>
          </td>
        </tr>
      </table>
    </div>
    <div v-else>
      There are no hot dogs.. Lets add one now!!! <br /><br />
      <router-link v-bind:to="{ name: 'NewPost' }" class="add_post_link">Add Hot Dog</router-link>
    </div>
    <div class="flex-container">
      <div class="unit">
        <div class="hotdog-unit">
          <div class="bread left"></div>
          <div class="hotdog">
            <div class="mustard"></div>
          </div>
          <div class="bread right"></div>
        </div>
        <div class="shadow"></div>
      </div>
    </div>
  </div>

</template>

<script>
import PostsService from '@/services/PostsService'
export default {
  name: 'posts',
  data () {
    return {
      posts: []
    }
  },
  mounted () {
    this.getPosts()
  },
  methods: {
    async getPosts () {
      const response = await PostsService.fetchPosts()
      this.posts = response.data.posts
    },
    async deletePost (id) {
      await PostsService.deletePost(id)
      this.getPosts()
      this.$router.push({ name: 'Posts' })
    }
  }
}
</script>
<style lang="scss" scoped>

  @import '../../src/assets/css/hotdog.css';

.table-wrap {
  width: 80%;
  margin: 0 auto;
  text-align: center;
  overflow: hidden;
}
table th, table tr {
  text-align: left;
}
table thead {
  background: #f2f2f2;
}
table tr td {
  padding: 10px;
}
table tr:nth-child(odd) {
  background: #f2f2f2;
}
table tr:nth-child(1) {
  background: #f9cb38;
  color: #CD4314;
}
a {
  color: #37BBD4;
  text-decoration: none;
}
a.add_post_link {
  background: #37BBD4;
  color: #fff;
  padding: 10px 80px;
  text-transform: uppercase;
  font-size: 12px;
  font-weight: bold;
}
  @media only screen and (max-width:768px) {
    .table-wrap {
      width: 100%;
    }
    .posts{
      width: 100%;
    }
  }
</style>
