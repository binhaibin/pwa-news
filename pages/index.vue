<template>
  <section class="section">
    <div class="container">
      <div class="columns is-multiline">
       <table>
      <thead>
        <tr>
          <td>name</td>
        </tr>
      </thead>
      <tbody>
        <tr v-for="music in posts" :key="music.id">
          <td> {{ music.thumbnail }}</td>
        </tr>
      </tbody>
    </table>
      </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios';
export default {
   data() {
    return {
      posts: [],
      errors: []
    }
  },

  // lấy dữ liệu khi component được tạo thành công
  created() {
    axios.get(`https://localhost:44391/api/Songs`)
    .then(response => {
      this.posts = response.data
    })
    .catch(e => {
      this.errors.push(e)
    })
  }
};
</script>