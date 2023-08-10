<template>
    <div class="hello">
      <h1>this is child page</h1>
      <h2>{{ msg }}</h2>
      <!-- <h3>{{ user.name }}</h3> -->
      <h3>{{ userinfo[0] }}</h3>
      <ol>
        <li v-for="x in userinfo" :key="x">{{x.name}}</li>
      </ol>

      <button v-on:click="callparent()">click me to call Function inside parent</button>

     
     
    </div>
  </template>
  
  <script>
  export default {
    name: 'ChildPage',

    props:{
        msg:String,
        // user:Object,
        userinfo:Object,
        callparent:Function,

    }
   
  }
  </script>