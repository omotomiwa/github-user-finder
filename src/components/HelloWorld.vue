<template>
  <div>
    <b-navbar class="navigation">
      <span style="font-size: 2em;  color: white;">
        <i class="fab fa-github"></i>
      </span>

      <b-navbar-nav class="search_box mx-auto">
        <b-nav-form variant="dark" type="dark">
          <b-form-input
            v-model="name"
            name="name"
            size="sm"
            class="mr-sm-2 search"
            placeholder="Search for User..."
          ></b-form-input>
          <b-button
            @click="reset"
            v-on:click="hello"
            size="sm"
            class="my-2 my-sm-0"
            >Search</b-button
          >
        </b-nav-form>
      </b-navbar-nav>
    </b-navbar>
    <div>
      <b-tabs content-class="mt-5" align="center">
        <b><i class="fas fa-atlas mx-auto fa-fw icon"></i></b>
        <b class="icon mx-auto">Respositories:</b>
        <b-badge
          variant="secondary text-dark-50"
          class="repoNumber icon mx-auto"
          pill
          v-for="(info, key1) in infos"
          :key="key1 + 10"
          >{{ info.public_repos }}</b-badge
        >
        <b-tabs title="hello"></b-tabs>
      </b-tabs>
    </div>

    <div class="imageContainer">
      <img
        class="avata"
        v-for="(info, key2) in infos"
        :key="key2 + 11"
        :src="info.avatar_url"
      />
       <h2 class="user" v-for="(info, keyz) in infos" :key="keyz + 17">
      <a :href="info.html_url" target="_blank"> {{ info.login }} </a>
    </h2>
    </div>

   
    <div class="container">
      <div class="card">
        <div class="blender"></div>
       
      </div>
    </div>

    <div class="repoContainer">
      <div class="repoList">
        <h3 class="repoName align"></h3>
        <i class="fas fa-circle fa-fw circle align">
          <p class="language"></p>
        </i>

        <br />
      </div>
      <div class="repoList2">
        <h3 class="repoName2 align"></h3>
        <i class="fas fa-circle fa-fw circle align">
          <p class="language2"></p>
        </i>

        <br />
      </div>
      <div class="repoList3">
        <h3 class="repoName3 align"></h3>
        <i class="fas fa-circle fa-fw circle align">
          <p class="language3"></p>
        </i>

        <br />
      </div>
      <div class="repoList4">
        <h3 class="repoName4 align"></h3>
        <i class="fas fa-circle fa-fw circle align">
          <p class="language4"></p>
        </i>

        <br />
      </div>
      <div class="repoList5">
        <h3 class="repoName5 align"></h3>
        <i class="fas fa-circle fa-fw circle align">
          <p class="language5"></p>
        </i>

        <br />
      </div>
    </div>

    <div class="footer">
      <b-nav align="center">
        <b-nav-item disabled class="leftNav px-2"
          >© 2020 GitHub, Inc</b-nav-item
        >
        <b-nav-item class="leftNav px-2">Terms</b-nav-item>
        <b-nav-item class="leftNav px-2">Privacy</b-nav-item>
        <b-nav-item class="leftNav px-2">Security</b-nav-item>
        <b-nav-item class="leftNav px-2">Status</b-nav-item>
        <b-nav-item class="leftNav px-2">Help</b-nav-item>
        <span style="font-size: 2em;  color: grey;">
          <i class="fab fa-github middleNav px-5"></i>
        </span>

        <b-nav-item class="rightNav px-2">Contact Github</b-nav-item>
        <b-nav-item class="rightNav px-2">Pricing</b-nav-item>
        <b-nav-item class="rightNav px-2">API</b-nav-item>
        <b-nav-item class="rightNav px-2">Training</b-nav-item>
        <b-nav-item class="rightNav px-2">Blog</b-nav-item>
        <b-nav-item class="rightNav px-2">About</b-nav-item>
      </b-nav>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",

  data() {
    return {
      name: "",
      infos: [],
      repos: [],
    };
  },

  methods: {
    hello() {
      let user = document.querySelector(".search").value;
      let fullname = user.split(" ").join("");
      let msg = "No Username Found";
      let showRepo = document.querySelector(".repoName");
      let showLanguage = document.querySelector(".language");

      let showRepo2 = document.querySelector(".repoName2");
      let showLanguage2 = document.querySelector(".language2");

      let showRepo3 = document.querySelector(".repoName3");
      let showLanguage3 = document.querySelector(".language3");

      let showRepo4 = document.querySelector(".repoName4");
      let showLanguage4 = document.querySelector(".language4");

      let showRepo5 = document.querySelector(".repoName5");
      let showLanguage5 = document.querySelector(".language5");
    

      const axios = require("axios");
      axios
        .get("https://api.github.com/users/" + fullname)
        .then((response) => (this.infos = response))

        .catch(function() {
          return alert(msg);
        });

      axios
        .get(`https://api.github.com/users/${fullname}/repos`)
        .then((res) => {
          let response1 = res.data[0].full_name;
          let response2 = res.data[0].language;

          let response3 = res.data[1].full_name;
          let response4 = res.data[1].language;

          let response5 = res.data[2].full_name;
          let response6 = res.data[2].language;

          let response7 = res.data[3].full_name;
          let response8 = res.data[3].language;

          let response9 = res.data[4].full_name;
          let response10 = res.data[4].language;

          showRepo.innerHTML = response1;
          showLanguage.innerHTML = response2;

          showRepo2.innerHTML = response3;
          showLanguage2.innerHTML = response4;

          showRepo3.innerHTML = response5;
          showLanguage3.innerHTML = response6;

          showRepo4.innerHTML = response7;
          showLanguage4.innerHTML = response8;

          showRepo5.innerHTML = response9;
          showLanguage5.innerHTML = response10;
        });
    
	
	let pS = document.querySelector(".blender");
	pS.innerHTML = "First 5 Repos...";




    
    
    },

   

    reset() {
      this.name = "";
    },
    


  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body {
  margin: 0;
  padding: 0;
  height: 100%;
}
h6 {
  font-size: 13px;
}
h3 {
  color: rgb(22, 11, 167);
}
.search {
  background-color: rgb(27, 26, 26);
  border: 1px solid rgb(156, 154, 154);
  font-family: Arial, Helvetica, sans-serif;
}
.navigation {
  background-color: rgb(27, 26, 26);
  height: 70px;
}
.icon {
  position: relative;
  left: 45%;
}

.imagecontainer {
  display: flex;
  justify-content: center;
  position: relative;
  min-height: 100vh;
}
.avata {
  border-radius: 50%;
  width: 20%;
  height: 20%;
  display: flex;
  justify-content: center;
  padding: 10px;
  position: relative;
  left: 40%;
}

.user {
  text-align: center;
  margin: auto;
  height: 10%;
  width: 15%;
}



.container {
	width: 75vw;
	margin: 0 auto;
}

.card {
	width: 60%;
	height: 70px;
	margin: 5vh;
	box-shadow: 4px 4px 1rem hsla(0,0%,0%, .2);
	
}

.blender{
  font-size: 2rem;
  text-align: center;
  font-family:  sans-serif;
  justify-content: center;
  margin: auto;
}


.circle {
  display: flex;
}
.repoContainer {
  position: relative;
  min-height: 100vh;
 
}
.repoList {
  margin: auto;
  width: 70%;
  height: 20%;
  background-color: whitesmoke;
  color: white;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  margin-top: 10px;
  border-radius: 5px;
  box-shadow: 4px 4px 1rem hsla(0,0%,0%, .2);
}
.repoList2 {
  margin: auto;
  width: 70%;
  height: 20%;
  background-color: whitesmoke;
  color: white;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  margin-top: 10px;
  border-radius: 5px;
  box-shadow: 4px 4px 1rem hsla(0,0%,0%, .2);
}
.repoList3 {
  margin: auto;
  width: 70%;
  height: 20%;
  background-color: whitesmoke;
  color: white;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  margin-top: 10px;
  border-radius: 5px;
  box-shadow: 4px 4px 1rem hsla(0,0%,0%, .2);
}
.repoList4 {
  margin: auto;
  width: 70%;
  height: 20%;
  background-color: whitesmoke;
  color: white;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  margin-top: 10px;
  border-radius: 5px;
  box-shadow: 4px 4px 1rem hsla(0,0%,0%, .2);
}
.repoList5 {
  margin: auto;
  width: 70%;
  height: 20%;
  background-color: whitesmoke;
  color: white;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  margin-top: 10px;
  border-radius: 5px;
  box-shadow: 4px 4px 1rem hsla(0,0%,0%, .2);
}

.align {
  margin-left: 10px;
   font-size: large;
}
p,
.fa-circle {
  margin-left: 10px;
  color: grey;
}

.footer {
  width: 100%;
  height: 40px;
  position: relative;
  bottom: 0;
  font-size: 12px;
}

/* mobile */
@media only screen and (min-device-width: 320px) and (max-device-width: 480px) and (-webkit-min-device-pixel-ratio: 2) and (orientation: portrait) {
 .avata {
    border-radius: 50%;
  width: 40%;
  height: 40%;
  display: flex;
  justify-content: center;
  padding: 10px;
  position: relative;
  left: 35%;
  }
  .user {
    position: relative;
    left: 1px;
    bottom: 50px;
    font-size: 1em;
  }
  .footer {
    width: 100%;
    height: 40px;
    position: relative;
    bottom: 0;
  }
}
/* ----------- iPhone 5, 5S, 5C and 5SE ----------- */

/* Portrait and Landscape */
@media only screen and (min-device-width: 320px) and (max-device-width: 568px) and (-webkit-min-device-pixel-ratio: 2) {
  .icon {
    position: relative;
    left: 30%;
  }
  .avata {
    border-radius: 50%;
  width: 40%;
  height: 40%;
  display: flex;
  justify-content: center;
  padding: 10px;
  position: relative;
  left: 35%;
  }
  .user {
    position: relative;
    left: 1px;
    bottom: 50px;
    font-size: 1em;
  }
  .card {
	width: 40vw;
	height: 70px;
	margin: 5vh;
	box-shadow: 4px 4px 1rem hsla(0,0%,0%, .2);
	
}

.blender{
  font-size: 10px;
  text-align: center;
  font-family:  sans-serif;
  justify-content: center;
  margin: auto;
}
  .footer {
    width: 100%;
    position: relative;
    bottom: 0;
  }
}
/* ----------- iPhone 6+, 7+ and 8+ ----------- */

/* Portrait and Landscape */
@media only screen and (min-device-width: 414px) and (max-device-width: 736px) and (-webkit-min-device-pixel-ratio: 3) {
  .avata {
    border-radius: 50%;
  width: 40%;
  height: 40%;
  display: flex;
  justify-content: center;
  padding: 10px;
  position: relative;
  left: 35%;
  }
  .user {
    position: relative;
    left: 1px;
    bottom: 50px;
    font-size: 1em;
  }
  
  .footer {
    width: 100%;
    position: relative;
    bottom: 0;
  }
}
/* ----------- iPhone X ----------- */

/* Portrait and Landscape */
@media only screen and (min-device-width: 375px) and (max-device-width: 812px) and (-webkit-min-device-pixel-ratio: 3) {
  .avata {
    border-radius: 50%;
  width: 40%;
  height: 40%;
  display: flex;
  justify-content: center;
  padding: 10px;
  position: relative;
  left: 35%;
  }
  .user {
    position: relative;
    left: 1px;
    bottom: 50px;
    font-size: 1em;
  }
  .footer {
    width: 100%;
    height: 40px;
    position: relative;
    bottom: 0;
  }
}

/* Tablets */
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (-webkit-min-device-pixel-ratio: 1) {
 .avata {
    border-radius: 50%;
  width: 40%;
  height: 40%;
  display: flex;
  justify-content: center;
  padding: 10px;
  position: relative;
  left: 30%;
  }
  .user {
    position: relative;
    left: 1px;
    bottom: 50px;
    font-size: medium;
  }
  .align {
  margin-left: 10px;
   font-size: large;
}
p,
.fa-circle {
  margin-left: 10px;
  color: grey;
}

  .footer {
    width: 100%;
    position: relative;
    bottom: 0;
    height: 40px;
  }
}
/* Portrait and Landscape  for ipad */
@media only screen and (min-device-width: 481px) and (max-device-width: 1024px) and (orientation: portrait) {
  /* For portrait layouts only */
  .icon {
    position: relative;
    left: 40%;
  }
.avata {
    border-radius: 50%;
  width: 40%;
  height: 40%;
  display: flex;
  justify-content: center;
  padding: 10px;
  position: relative;
  left: 30%;
  }
  .user {
    position: relative;
    left: 1px;
    bottom: 50px;
    font-size: medium;
  }
  .align {
  margin-left: 10px;
   font-size: large;
}
p,
.fa-circle {
  margin-left: 10px;
  color: grey;
}
  .footer {
    width: 100%;
    position: relative;
    bottom: 0;
    height: 40px;
  }
}
/* Portrait and Landscape  for ipad pro */
@media only screen and (min-device-width: 834px) and (max-device-width: 1112px) and (-webkit-min-device-pixel-ratio: 2) {
  .icon {
    position: relative;
    left: 40%;
  }
 .avata {
    border-radius: 50%;
  width: 40%;
  height: 40%;
  display: flex;
  justify-content: center;
  padding: 10px;
  position: relative;
  left: 30%;
  }
 .user {
    position: relative;
    left: 1px;
    bottom: 50px;
    font-size: x-large;
  }
  .align {
  margin-left: 10px;
   font-size: x-large;
}
p,
.fa-circle {
  margin-left: 10px;
  color: grey;
}
  .footer {
    width: 100%;
    position: relative;
    bottom: 0;
    height: 40px;
  }

  /* ----------- Google Pixel XL ----------- */

  /* Portrait and Landscape */
  @media screen and (device-width: 360px) and (device-height: 640px) and (-webkit-device-pixel-ratio: 4) {
    .avatar {
      width: 170px;
      height: 170px;
      border-radius: 90px;
      position: relative;
      left: 6%;
    }
    .footer {
      width: 100%;
      position: relative;
      bottom: 0;
      height: 40px;
    }
  }
}
</style>
