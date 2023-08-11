<template>
<h1>contact page</h1>
<h2>contact number :{{ con_num }}</h2>
<h3>email :{{ getDetails().email}}</h3>
<button v-on:click="getCount()">click {{ count }}</button>


<!-- 2 way binding eg1 -->
<input type="text" v-model="count1">
<h2>{{ count1 }}</h2>


<!-- 2 way binding eg2  -->
<div>
<input type="text" placeholder="enter username" v-model="username">
<input type="password" placeholder="enter password" v-model="password">
<button v-on:click="getData()">get username $ pw</button>
</div>

<!-- if else condition in vue -->
<div>
  <h1 v-if="show" >hello world.....</h1>
  <button v-on:click="changeBool()">hide or show</button>
</div>

<!-- for loop in vue  -->
<ul>
  <li v-for="item in languages" :key="item">{{ item }}</li>
</ul>

<ol>
  <li v-for="item in userinfo" :key="item.dept" >{{ item.dept }}</li>
</ol>

<!-- importing child component and utility of props  -->
<ChildPage msg="hello this is example to show use of props" :userinfo="userinfo" :callparent="parentfunc"/>

<!-- html binding -->
<div v-html="tag1"></div>

<!-- class binding -->
<h1 :class="{green:colourfull}">this is the example of class binding </h1>

<!-- Ref in vue js -->
<input type="text" ref="input"/>
<button v-on:click="getRef">click me for ref</button>

<br>
<br>
<!-- simple forms in vue js -->
<!-- check out code step by step 
we will be using v-model over here -->


<!-- lifecycle in vue js -->
<!-- beforeCreate()  >  data()   >   created() -->
<!-- this functions works on ui  -->







</template>

<script>
import ChildPage from './ChildPage.vue'
export default {
    name: 'ContactPage',
    components:{
      ChildPage
    },
    data() {
        return {
            con_num: '6296755931',
            count: 0,
            count1:'',
            username:null,
            password:null,
            show:true,
            languages:["c++","java","c#","solidity","python","javascript"],
            userinfo:[{name:"sayan",dept:"ece"},{name:"ranit",dept:"ce"},{name:"jishnu",dept:"me"}],
            user:{name:"e9",dept:"internet company"},
            tag1:"<h1>this is html tag</h1>",
            colourfull:true,


        }

    },

    methods: {
        getDetails() {
            return {

                name: "sayan",
                email: "acharjeesayandip00@gmail.com",
                contact: this.con_num,
            }

        },
        

        getCount() {
           this.count=this.count+1;
        },
        getData()
        {
          console.log("values are",this.username, this.password)
        },
        changeBool()
        {
          this.show=!this.show
        },
        parentfunc()
        {
          console.warn("hello from parent side")
        },
        getRef()
        {
           this.$refs.input.focus();
      let val=this.$refs.input.value;
      console.log(val);
      this.$refs.input.style.color="red";
        }



    }

}
</script>

<style>
.green{
  color: #23d80b;
}
</style>
