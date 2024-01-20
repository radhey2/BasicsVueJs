<template>
  <div>
    <h2>Hello {{ name }} Department is {{ dept }}</h2>
    <h3 v-text="company"></h3>
    <h3 v-html="role"></h3>
    <h3 v-bind:id="empId">EmpId is SPICE1234</h3>
    <button v-bind:disabled="isDisabled">Click</button>
    <h3 class="underLine">UnderLine Text</h3>
    <h3 v-bind:class="status">Status</h3>
    <h3 v-bind:class="isPromoted && 'promoted'">Promoted Movies</h3>
    <h3 v-bind:class="isSoldOut ? 'sold-out' : 'new-movie'">Soldout ? movie</h3>
    <h3 v-bind:class="['new-movie', 'promoted']">Newly promoted movie</h3>
    <h3 v-bind:class="[isPromoted && 'promoted', isSoldOut ? 'sold-out' : 'new']">
      Array conditional movie
    </h3>
    <h3
      v-bind:class="{
        promoted: isPromoted,
        new: !isSoldOut,
        'sold-out': isSoldOut,
      }"
    >
      Object conditional movie
    </h3>
    <h3
      v-bind:style="{
        color: highlightcolor,
        fontSize: headersize + 'px',
        padding: '20px',
      }"
    >
      Inline Style
    </h3>
    <h3 v-bind:style="headerStyleObject">Style Object</h3>
    <h3 :style="[baseStyleObject, successStyleObject]">Success Style Object</h3>

    <!-- 
  Conditional randering 
  v- show element persent in dom after false exp but v-if element is remove from dom after false exp
  -->
    <h3 v-if="num === 0">Number is {{ num }}</h3>
    <h3 v-if="num < 0">Number is Negative</h3>
    <h3 v-else>Number is {{ num }}</h3>
    <template v-if="display">
      <h2>Radhey</h2>
      <h2>Vuejs</h2>
      <h2>SpiceMoney</h2>
    </template>

    <!-- 
    List rendering using v- for directives its like loops
   -->
    <h2 v-for="name in names" :key="name">{{ name }}</h2>
    <!-- 
    name with index values
    -->
    <h2 v-for="(name, index) in names" :key="name">{{ index }} {{ name }}</h2>
    <!-- 
  Array of Object using v-for
  -->
    <h2 v-for="name in fullNames" :key="name">
      {{ name.firstName }} {{ name.lastName }}
    </h2>

    <!-- 
    Array of Arrays
    -->
    <div v-for="actor in actors" :key="actor">
      <h4>Actor Name : {{ actor.name }}</h4>
      <ul>
        <li v-for="movie in actor.movies" :key="movie">
          {{ movie }}
        </li>
      </ul>
    </div>
    <h3 v-for="(info, key, index) in myInfo" :key="info">
      {{ index }} {{ key }} {{ info }}
    </h3>
    <h3 v-for="name in names" :key="name">
      {{ name }}
      <hr />
    </h3>

    <!-- 
    List Conditional rendering
   -->
    <template v-for="name in names" :key="name">
      <h3 v-if="name === 'bill'">
        {{ name }}
      </h3>
    </template>

    <!-- 
    Calling add method
   -->
    <h3>add method {{ add(2, 3) }}</h3>

    <!-- 
    Calling multiply method
    need to use this keyword while accessing the data peoperty in method but  we can
    directly access in template tag like basevalue
   -->
    <h3>multiply Method {{ multiply(basevalue) }}</h3>

    <!-- 
    Event Handling using v-on directive
    like click mouse hover etc
    -->
    <h2>{{ name }}</h2>
    <div>
      <button v-on:click="name = 'Batman'">Change Name</button>
      <hr />
      <button v-on:mouseover="name = 'jhon'">Change Name</button>
      <br />

      <h2>{{ count }}</h2>
      <div>
        <!-- 
        Inline Event Handler
       -->
        <!-- <button v-on:click="count = count + 1">Increment</button> 
      <button v-on:click="count = count - 1">Decrement</button> -->

        <button v-on:click="increment(1, $event)">Increment</button>
        <button v-on:click="decrement(1)">Decrement</button>

        <!-- 
          ShortHand syntex for v-on
         -->
        <button @:click="increment(2, $event)">Increment 2</button>
        <button @:click="decrement(2)">Decrement 2</button>
      </div>
    </div>

    <!-- 
    Form Handling v-model-> use for two way binding from tamplate to script and vice versa
    -->
    <br />
    <div>
      <pre>{{ JSON.stringify(formValues, null, 2) }}</pre>
    </div>
    <form @submit="submitForm">
      <div>
        <label for="name">Name</label>
        <input type="text" id="name" v-model.trim.lazy="formValues.name" />
      </div>

      <div>
        <label for="profile">Profile Summary</label>
        <textarea id="profile" v-model="formValues.profileSummary"></textarea>
      </div>

      <div>
        <label for="country">country</label>
        <select name="country" id="country" v-model="formValues.country">
          <option value="">Select Country</option>
          <option value="India">India</option>
          <option value="Australia">Australia</option>
          <option value="America">America</option>
          <option value="Japan">Japan</option>
        </select>
      </div>

      <div>
        <label for="job-location">Job Location</label>
        <select
          name="job-location"
          id="job-location"
          multiple
          v-model="formValues.jobLocation"
        >
          <option value="India">India</option>
          <option value="Australia">Australia</option>
          <option value="America">America</option>
          <option value="Japan">Japan</option>
        </select>
      </div>

      <div>
        <input
          type="checkbox"
          id="remotework"
          v-model="formValues.remotework"
          true-value="yes"
          false-value="no"
        />
        <label for="remotework">open to remote work</label>
      </div>

      <div>
        <input type="checkbox" id="html" value="html" v-model="formValues.skillset" />
        <label for="html">HTML</label>
        <input type="checkbox" id="CSS" value="CSS" v-model="formValues.skillset" />
        <label for="CSS">CSS</label>
        <input type="checkbox" id="JS" value="JS" v-model="formValues.skillset" />
        <label for="JS">HTML</label>
        <div>
          <label for="age">AGE</label>
          <input
            @keyup.enter="submitForm"
            type="number"
            id="age"
            v-model.number="formValues.age"
          />
        </div>

        <div><button>Submit</button></div>
      </div>
    </form>
    <h2 v-once>{{ name }}</h2>
    <button @click="name = 'Batman'">Change name</button>
    <h3 v-pre>{{ name }}</h3>
    <h3>{{ completename }}</h3>
    <!-- <h3>Total without computed : {{ items.reduce((total,curr) =>(total = total + curr.price),0) }} </h3> -->
    <h3>Totalwith Computed : {{ total }}</h3>
    <button @click="items.push({id: 4,price : 500,title: 'movie'})">Add item</button>
  </div>
</template>

<script>
export default {
  name: "App",
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
      highlightcolor: "orange",
      headersize: 40,
      headerStyleObject: {
        color: "yellow",
        fontSize: 40 + "px",
        padding: "20px",
      },
      baseStyleObject: {
        fontSize: "50px",
        padding: "100px",
      },
      successStyleObject: {
        color: "green",
        backgroundColor: "ligtgreen",
        border: "1px solid green",
      },
      num: -10,
      display: true,
      names: ["bruce", "bill", "radhey"],
      fullNames: [
        { firstName: "Bill", lastName: "Jam" },
        { firstName: "sam", lastName: "sharma" },
        { firstName: "jhon", lastName: "cena" },
      ],
      actors: [
        {
          name: "Amir",
          movies: ["Three Idiots", "PK", "andaz apna apna"],
        },
        {
          name: "Salman",
          movies: ["jai ho", "Tiger zinda h", "andaz apna apna"],
        },
        {
          name: "Shahruk",
          movies: ["KKKG", "Kal ho na ho", "jab tak h jaan"],
        },
      ],
      myInfo: {
        name: "Radhey",
        course: "vuejs",
        type: "development",
      },
      baseMultiplier: 5,
      basevalue: 10,
      count: 0,
      formValues: {
        name: "",
        profileSummary: "",
        country: "",
        jobLocation: [],
        remotework: "no",
        skillset: [],
        age: null,
      },
      firstName: "jhon",
      lastName: "jay",
      items: [
        {
          id: 1,
          price: 100,
          title: "TV",
        },
        {
          id: 2,
          price: 200,
          title: "Phone",
        },
        {
          id: 3,
          price: 300,
          title: "car",
        },
      ],
    };
  },
  methods: {
    add(a, b) {
      return a + b;
    },
    multiply(num) {
      return num * this.baseMultiplier;
    },
    increment(num, event) {
      this.count += num;
      console.log("event is :", event);
    },
    decrement(num) {
      this.count -= num;
    },
    submitForm(event) {
      event.preventDefault();
      console.log("Form Values ", this.formValues);
    },
  },
  computed: {
    completename() {
      return `${this.firstName} ${this.lastName}`;
    },
    total() {
      return this.items.reduce((total, curr) => (total = total + curr.price), 0);
    }
  },
};
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

.underLine {
  text-decoration: underline;
}

.promoted {
  font-style: italic;
}

.new-movie {
  color: greenyellow;
}

.sold-out {
  color: red;
}
</style>
