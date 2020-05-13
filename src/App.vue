<template>
  <div id="app">
    <div class="topnav">
      <a class="active" href="#home" >Home</a>
      <a href="#contact" >Contact</a>
      <a href="#about">About</a>
    </div>
    <div>
      <table class="tablecss">
        <thead>
          <tr>
            <th>Country</th>
            <th>Active</th>
            <th>Cases</th>
            <th>deaths</th>
            <th>deathsPerOneMillion</th>
            <th>recovered</th>
            <th>testsPerOneMillion</th>
            <th>todayCases</th>
            <th>todayDeaths</th>
            <th>totalTests</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(id,index) in tabledata" v-bind:key ="index">
            <td>{{ id.country }}</td>
            <td>{{ id.active }}</td>
            <td>{{ id.cases }}</td>
            <td>{{ id.deaths }}</td>
            <td>{{ id.deathsPerOneMillion }}</td>
            <td>{{ id.recovered }}</td>
            <td>{{ id.testsPerOneMillion }}</td>
            <td>{{ id.todayCases }}</td>
            <td>{{ id.todayDeaths }}</td>
            <td>{{ id.totalTests }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>


<script>
export default {
  name: "app",
  data() {
    return {
      tabledata: {}
    };
  },
  created() {
    this.fetchCharacter();
  },
  methods: {
    fetchCharacter() {
      fetch(`https://coronavirus-19-api.herokuapp.com/countries`, {
        method: "GET"
      })
        .then(response => response.json())
        .then(json => (this.tabledata = json));
    }
  }
};
</script>