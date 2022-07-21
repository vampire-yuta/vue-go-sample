<template>
  <div class="hello">
    <button @click="sendRequest">リクエスト送信</button>
    <h1>取得結果</h1>
    <p>GET:<br />{{edinet}}</p>
  </div>
</template>

<script>
import axios from "axios";

const BaseURL = "http://localhost:1323";

export default {
  name: "App",
  data: () => {
    return {
      edinet: ""
    };
  },
  methods: {
    sendRequest: async function () {
      const instance = axios.create({
        baseURL: BaseURL,
      });
      const getRequestNoParam = await instance({
        method: "get",
        url: "/hello",
      });

      this.edinet = getRequestNoParam.data;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
