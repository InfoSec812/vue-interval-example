<template>
  <div class="hello">
    <ul>
      <li>{{ chartData.values.macrohard }}</li>
      <li>{{ chartData.values.blackcoat }}</li>
      <li>{{ chartData.values.divinator }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      chartData: {
          indices: [new Date()],
          values: {
              'macrohard': 20,
              'blackcoat': 50,
              'divinator': 30
          }
      },
      intervalId: 0
    }
  },
  computed: {
      stockData() {
          return this.chartData;
      }
  },
  methods: {
      updateData: () => {
        console.log("Data: " + JSON.stringify(this.data));  // Shows up as undefined.
/*        for (var prop in this.$data.chartData.values) {
            if (this.$data.chartData.values.hasOwnProperty(prop)) {
                let holder = parseFloat(this.$data.chartData.values[prop]) + parseFloat(Math.random().toFixed(2));
            }
        }
        this.$data.chartData.indices = [new Date()];*/
      }
  },
  mounted () {
    setInterval(() => {
        this.intervalId = this.updateData()
    }, 1200);
  },
  beforeDestroy () {
    clearInterval(this.intervalId);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
