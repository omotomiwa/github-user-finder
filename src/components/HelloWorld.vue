<template>
  <div>
    <b-navbar class="navigation">
      <span style="font-size: 2em;  color: white;">
        <i class="fab fa-github"></i>
      </span>
      
      <b-navbar-nav class="search_box mx-auto">
        <b-nav-form variant="dark" type="dark">
          <b-form-input
          v-model="name" name="name"
            size="sm"
            class="mr-sm-2 search"
            placeholder="Search for User..."
            
          ></b-form-input>
          <b-button  @click= "reset" v-on:click= "hello"  size="sm" class="my-2 my-sm-0"
         

            >Search</b-button
          >
        </b-nav-form>
      </b-navbar-nav>
      
    </b-navbar>
    <div>
      <b-tabs content-class="mt-5"  align="center">
        <b><i class="fas fa-atlas mx-auto icon"></i></b>
        <b class="icon mx-auto">Respositories:</b>
        <b-badge variant="secondary text-dark-50" class="repoNumber icon mx-auto" pill>0</b-badge>
        <b-tabs title="hello"></b-tabs>
      </b-tabs>
    </div>
   
    
      <div class="imageContainer ">
        <img
          class="avatar"
          src="https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80"
        />
         
      </div>
      <b class="user">Username</b>
      <div class="repoContainer">
          <b-list-group class="repoList w-75 h-75">
        <b-list-group-item align="left" class="repoList w-75 h-75">
          <b-link href="#foo" disabled>Loren Ipsum</b-link><br /><br />
          <i class="fas fa-circle circle">
            <h6>TypeScript</h6>
          </i>
        </b-list-group-item> </b-list-group
      ><br />
      <b-list-group class="repoList w-75 h-75">
        <b-list-group-item align="left" class="repoList w-75 h-75">
          <b-link href="#foo" disabled>Loren Ipsum</b-link><br /><br />
          <i class="fas fa-circle circle">
            <h6>TypeScript</h6>
          </i>
        </b-list-group-item> </b-list-group
      ><br />
      <b-list-group class="repoList w-75 h-75">
        <b-list-group-item align="left" class="repoList w-75 h-75">
          <b-link href="#foo" disabled>Loren Ipsum</b-link><br /><br />
          <i class="fas fa-circle circle">
            <h6>TypeScript</h6>
          </i>
        </b-list-group-item> </b-list-group
      ><br />
      <b-list-group class="repoList w-75 h-75">
        <b-list-group-item align="left" class="repoList w-75 h-75">
          <b-link href="#foo" disabled>Loren Ipsum</b-link><br /><br />
          <i class="fas fa-circle circle">
            <h6>TypeScript</h6>
          </i>
        </b-list-group-item> </b-list-group
      ><br />
      <b-list-group class="repoList w-75 h-75">
        <b-list-group-item align="left" class="repoList w-75 h-75">
          <b-link href="#foo" disabled>Loren Ipsum</b-link><br /><br />
          <i class="fas fa-circle circle">
            <h6>TypeScript</h6>
          </i>
        </b-list-group-item> </b-list-group
      ><br />
      </div>
      <div class="footer">
        <b-nav align= "center">
    <b-nav-item disabled class="leftNav px-2">© 2020 GitHub, Inc</b-nav-item>
    <b-nav-item class="leftNav px-2">Terms</b-nav-item>
    <b-nav-item class="leftNav px-2">Privacy</b-nav-item>
    <b-nav-item  class="leftNav px-2">Security</b-nav-item>
     <b-nav-item  class="leftNav px-2">Status</b-nav-item>
    <b-nav-item  class="leftNav px-2">Help</b-nav-item>
     <span style="font-size: 2em;  color: grey;">
        <i class="fab fa-github middleNav px-5"></i>
      </span>

  
    <b-nav-item class="rightNav px-2">Contact Github</b-nav-item>
    <b-nav-item class="rightNav px-2">Pricing</b-nav-item>
    <b-nav-item  class="rightNav px-2">API</b-nav-item>
     <b-nav-item  class="rightNav px-2">Training</b-nav-item>
    <b-nav-item  class="rightNav px-2">Blog</b-nav-item>
     <b-nav-item  class="rightNav px-2">About</b-nav-item>
    
  </b-nav>
      </div>
     
     
  
  
  </div>
</template>

<script>

export default {
  name: "HelloWorld",

 
   
  data(){
    return{
       name: '',

    }
    
     
  
    
  },
 
  methods:{
    hello(){
       let user= document.querySelector(".search").value;
       let fullname = user.split(" ").join("")
    
     const axios= require("axios");
  axios.get("https://api.github.com/users/"+fullname)
       .then(response => console.log(response));
        
    
     

      
      
    },
    reset(){
       this.name="";

    }
    
    
  }
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h6 {
  font-size: 13px;
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
.icon{
  position: relative;
  left: 45%;
}
.avatar {
  background-color: rgb(36, 32, 32);
  width: 270px;
  height: 270px;
  border-radius: 50%;
  position: relative;
  bottom : 40px;
  left: 10%;
  
}

.user {
  position: relative;
  left: 11%;
  bottom: 30px;
  
  
}
.circle {
  display: flex;
}
.repoContainer{
display:absolute;
left: 50%;

}
.repoList{
  width: 40%;
 
  
 
}
.footer{
    width: 100%;
    height: 40px;
   
   font-size: 12px;
}


/* mobile */
@media only screen and (min-device-width: 320px) and (max-device-width: 480px) and (-webkit-min-device-pixel-ratio: 2) and (orientation: portrait) {
  .avatar {
    width: 60px;
    height: 60px;
    border-radius: 70px;
    
  }
  .user {
    position: relative;
    
  }
  .footer{
    width: 100%;
    height: 40px;
}
}
/* ----------- iPhone 5, 5S, 5C and 5SE ----------- */

/* Portrait and Landscape */
@media only screen and (min-device-width: 320px) and (max-device-width: 568px) and (-webkit-min-device-pixel-ratio: 2) {
  .icon{
    position: relative;
    left : 30%;
  }
  .avatar {
    width: 60px;
    height: 60px;
    border-radius: 70px;
    position: relative;
    left: 10px;
    bottom: 60px;
    
  }
  .user{
    
    position: relative;
    left: 1px;
    bottom: 10px;
    font-size: 1em;
    
  }
 .footer{
    width: 100%;
    height: 40px;
      
}

  
}
/* ----------- iPhone 6+, 7+ and 8+ ----------- */

/* Portrait and Landscape */
@media only screen 
  and (min-device-width: 414px) 
  and (max-device-width: 736px) 
  and (-webkit-min-device-pixel-ratio: 3) { 
    .footer{
    width: 100%;
    height: 40px;
      
}
}
/* ----------- iPhone X ----------- */

/* Portrait and Landscape */
@media only screen 
  and (min-device-width: 375px) 
  and (max-device-width: 812px) 
  and (-webkit-min-device-pixel-ratio: 3) { 
     .footer{
    width: 100%;
    height: 40px;
      
}


}

/* Tablets */
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (-webkit-min-device-pixel-ratio: 1) {
  .avatar {
    width: 150px;
    height: 150px;
    border-radius: 70px;
    position: relative;
    left: -250px;
    bottom: 50px;
  }
  .footer{
    width: 100%;
    height: 40px;
}
}
/* Portrait and Landscape  for ipad */
@media only screen and (min-device-width: 481px) and (max-device-width: 1024px) and (orientation:portrait) {
  /* For portrait layouts only */
  .icon{
    position: relative;
    left:40%;
  }
  .avatar {
    width: 150px;
    height: 150px;
    border-radius: 80px;
    position: relative;
    left: 5%;
   
  }
  .user{
    position: relative;
    right:30px;

    
  }
  .footer{
    width: 100%;
    height: 40px;
}
}
/* Portrait and Landscape  for ipad pro */
@media only screen and (min-device-width: 834px) and (max-device-width: 1112px) and (-webkit-min-device-pixel-ratio: 2) {
  .icon{
    position: relative;
    left: 40%;
  }
  .avatar {
    width: 170px;
    height: 170px;
    border-radius: 90px;
    position: relative;
    left: 6%;
   
  }
   .user{
    position: relative;
    margin-right: 3px;

    
  }
  .footer{
    width: 100%;
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
    .footer{
    width: 100%;
    height: 40px;
}
  }
}
</style>

 