<template>
  <div> <h2>Hello {{ name }} Department is {{ dept }}</h2>
  <h3 v-text="company"></h3>
  <h3 v-html="role"></h3>
  <h3 v-bind:id="empId">EmpId is SPICE1234</h3>
  <button v-bind:disabled="isDisabled">Click</button>
  <h3 class="underLine">UnderLine Text</h3>
  <h3 v-bind:class="status">Status</h3>
  <h3 v-bind:class="isPromoted && 'promoted'" >Promoted Movies</h3>
  <h3 v-bind:class="isSoldOut ? 'sold-out' : 'new-movie'">Soldout ? movie </h3>
  <h3 v-bind:class="['new-movie', 'promoted']">Newly promoted movie</h3>
  <h3 v-bind:class="[isPromoted && 'promoted', isSoldOut ? 'sold-out' : 'new']">Array conditional movie</h3>
   <h3 v-bind:class="{
    promoted : isPromoted,
    new : !isSoldOut,
    'sold-out' : isSoldOut
   }">Object conditional movie</h3>
  <h3 v-bind:style="{
    color : highlightcolor,
    fontSize : headersize + 'px',
    padding : '20px'
  }">Inline Style</h3>
  <h3 v-bind:style="headerStyleObject">Style Object</h3>
  <h3 :style="[baseStyleObject,successStyleObject]">Success Style Object</h3>
  </div>

</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      name: "Radhey",
      dept: "CMS",
      company: "Spicemoney",
      role: "<b>Software Engineer</b>",
      empId: "id",
      isDisabled: true,
      status: "active",
      isPromoted: true,
      isSoldOut: false,
      highlightcolor: 'orange',
      headersize: 40,
      headerStyleObject: {
         color: 'yellow',
        fontSize: 40 + 'px',
        padding: '20px'
      },
      baseStyleObject: {
         fontSize: '50px',
        padding: '100px'
      },
      successStyleObject: {
        color: 'green',
        backgroundColor: 'ligtgreen',
        border : '1px solid green'
      }
    }
  },
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.underLine{
  text-decoration: underline;
}

.promoted{
  font-style: italic;
}

.new-movie{
  color: greenyellow;
}

.sold-out{
  color: red;
}
</style>
