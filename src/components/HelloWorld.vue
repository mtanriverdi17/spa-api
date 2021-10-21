<template>
  <div class="hello">
    <h1>Mehmet Tanriverdi Facebok-Api Deneme</h1>
    <a href="javascript:void(0)" v-on:click="denemeRequest">Send Request</a>
    <br />
    <img
      :src="deneme"
      alt="selam"
      id="image"
      style="width: 360px; height:360px"
    />
  </div>
</template>

<script>
import $ from "jquery";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      deneme: "https://via.placeholder.com/150",
    };
  },

  methods: {
    sendRequest() {
      var settings = {
        url:
          "https://graph.instagram.com/18137607199156704?fields=id,media_type,media_url,username,timestamp&access_token=IGQVJWQXNRTzhibFNFWG1KU2d1YkNjWGhhY3NqS0VOZA3pRQXQ5aDNGSHMtUVRCX0Ntb3VrUFV1N2ZAkUlNmQjZAsckFpcTRQSDRreHQtLWF0OGY3ZAWxfRFZAOR3luOVdsMVlDSHJqTlNleGNnLVgwRkt1WQZDZD",
        method: "GET",
        timeout: 0,
      };

      $.ajax(settings).done(function(response) {
        $("#image").attr("src", response.media_url);
      });
    },
    async denemeRequest() {
      const res = await fetch("api/question");
      const data = await res.json();
      console.log(data);
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
