<template>
  <div id="app">
    {{ counter }}<br/>
    <button v-on:click="counter=counter+1">Click1</button><br/>
    <button v-on:click="clicked">Click2</button>
    <!--v-on:click ตัวย่อคือ @click-->
    <hr />
    <h1>{{ message }}</h1>
    <br />
    <span v-text="message"></span>
    <hr />

    <input type="text" v-model="message" />
    <hr />
    <h1 v-show="isShow">Hello!</h1>

    <hr />
    <div v-bind:key="emp.id" v-for="emp in employees">
      {{ emp.NAME }}
      <span v-if="emp.SALARY > 90000">⭐⭐⭐</span>
      <span v-else-if="emp.SALARY >= 30000">⭐⭐</span>
      <span v-else>⭐</span>
    </div>

    <hr />
    <div v-bind:key="emp.id" v-for="emp in employees">
      <span
        v-bind:class="
          emp.SALARY > 90000 ? 'high' : emp.SALARY >= 30000 ? 'medium' : 'low'
        "
      >
        {{ emp.NAME }}
      </span>

      <span v-if="emp.SALARY > 90000">⭐⭐⭐</span>
      <span v-else-if="emp.SALARY >= 30000">⭐⭐</span>
      <span v-else>⭐</span>
    </div>
    <a v-bind:href="urlYT">Youtube</a>
    <hr />
    <img
      v-bind:src="require('@/assets/images/' + picture + '.png')"
      width="500px"
    />
<hr/>
<select v-model="message">
<option value="Bread">Bread</option>
<option value="Candy">Candy</option>
<option value="Coke">Coke</option>

</select>
<hr/>
<textarea v-model="message"></textarea>

  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      counter:0,
      picture: "a",
      urlYT: "https://www.youtube.com/?gl=TH",
      message: "สวัสดี",
      isShow: true,
      employees: [
        { ID: 1, NAME: "SUPHAKIN", SALARY: 90001 },
        { ID: 2, NAME: "NANI", SALARY: 70000 },
        { ID: 3, NAME: "YUI", SALARY: 10 },
      ],
    };
  },
  methods:{
      clicked: function(){
        this.counter=this.counter+2;
      }
    }
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
.high {
  color: red;
}
.medium {
  color: green;
}
.low {
  color: blue;
}
</style>
