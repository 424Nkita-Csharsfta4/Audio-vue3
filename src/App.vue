<template>
  <div class="app-container p-3 bg-black m-auto">
    <SongList />
  </div>
</template>

<script>
import SongList from './components/SoundList.vue';
export default {
  name: 'App',
  components: {
    SongList
  }
}
</script>

<style>
.app-container {
  width: 550px;
  height: 500px;
  border-radius: 15px;
  border: 1px solid rgb(112, 56, 126);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 20px;
  color: rgba(84, 255, 133, 0.678);
}
span{
  color: rgba(151, 120, 228, 0.745);
}
body{
  background-color: rgb(39, 38, 38);
    box-sizing: border-box;
    color: rgba(78, 23, 198, 0.437);
}
button{
  width: 50px;
  height: 25px;
    border-radius: 5px;
    background-color: rgb(112, 56, 126);
    box-shadow: 0px 10px 30px rgb(190, 144, 201);
}


</style>
