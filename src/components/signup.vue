<template>
  <form>
      <label>Email</label>
      <input type="email" v-model="email">

      <label>Password</label>
      <input type="password" v-model="password">
  </form>
  <p>email: {{ email }}</p>
  <p>password: {{ password }}</p>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: ''
    }
}
}
</script>

<style>
form{
    max-width: 450px;
    margin: 10px auto;
    padding: 40px;
    background: white;
    border-radius: 10px;
    text-align: left;
}
label{
    display: inline-block;
    font-weight: bold;
    font-size: 0.5em;
    font-family: 'Times New Roman';
    color: rgb(160, 160, 160);
    margin: 25px 0 15px;
    text-transform: uppercase;
    letter-spacing: 1px;
}
input{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid rgb(160, 160, 160);
    color: #555;  
}
p{
    color: white;
}
</style>