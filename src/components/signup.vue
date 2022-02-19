<template>
  <form>
      <label>Email</label>
      <input type="email">
  </form>
</template>

<script>
export default {

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
    font-size: 1.5em;
    font-family: 'Times New Roman';
    color: rgb(161, 161, 161);
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
    border-bottom: 2px solid rgb(206, 206, 206);
    color: #555;  
}
</style>