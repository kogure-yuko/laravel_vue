<template>
<div>
  <div>
  <h1>ユーザー作成</h1>
  <form @submit.prevent="createUser">
    <div class="form-group">
      <label for="name">NAME:</label>
      <input v-model="user.name">
    </div>
    <div class="form-group">
      <label for="email">EMAIL:</label>
      <input v-model="user.email">
    </div>
    <div class="form-group">
      <label for="password">PASSWORD:</label>
      <input type="password" v-model="user.password">
    </div>
    <button type="submit">作成</button>
  </form>
  </div>
</div>
</template>

<script>
export default {
  data(){
    return {
      user:{
        name:'',
        email:'',
        password:''
      }
    }
  },
  methods:{
    createUser(){
      axios.post('/api/user', {
        user: this.user
        })
      .then(response =>{
        this.user = response.data.user;
        this.$router.push({ name: 'user'})
      })
      .catch(error => console.log(error));
    },
  }
}
</script>