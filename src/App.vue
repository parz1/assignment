<template>
  <div id="app">
    <ul>
      <li id="cheats">{{list[0]}}</li>
    </ul>
  </div>
</template>

<script src="vue.min.js"></script>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      list: []
    };
  },
  methods: {
    getData: function() {
      //   axios.get('http://ksp.debug.online:6703/?tdsourcetag=s_pctim_aiomsg',{
      //     headers:"Access-Control-Allow-Origin: *"
      //   })
      //   .then(response => {

      //       this.list[0]=response.data;
      //       console.log(response.data);
      //   })
      //   .catch(response => {
      //       console.log('error');
      //   });
      var instance = axios.create();
      instance.defaults.timeout = 2500;
      instance
        .get("http://ksp.debug.online:6703/", {
          timeout: 5000,
          headers: { "Access-Control-Allow-Origin": "*" }
        })
        .then(response => {
          this.list[0] = response.data;
          console.log(response.data);
        })
        .catch(response => {
          console.log("error");
        });
    }
  },
  mounted() {
    this.getData();
  }
};
</script>

//document.getElementById("cheats").innerHTML="cheats:"+JSON.stringify(response.data);
<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
