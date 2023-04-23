<template>
  <div>
    <h1>Distribution de nombres :</h1>
    <table class="graphic">
      <tr>
        <td v-for="(occurrence, index) in occurrences" :key="index">
          <tr class="graphic-occurrences">
            <td>
              <tr>
                <td :style="{height : occurrence + '%'}">{{ occurrence }}</td>
              </tr>
            </td>
          </tr>
          <tr class="graphic-index">{{ index + 1 }}</tr>
        </td>
      </tr>
    </table>
    <button @click="getRandomIntegerSet">Refresh</button>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'DistributionNumbers',
  data() {
    return {
      numbers: [],
      occurrences: []
    }
  },
  mounted() {
    this.getRandomIntegerSet()
  },
  methods:{
    //Recupération du set de donnée via l'API 
    getRandomIntegerSet(){
      axios.get('https://www.random.org/integer-sets/?sets=100&num=9&min=1&max=9&seqnos=off&commas=on&sort=off&order=index&format=plain')
      .then(response => {
        this.numbers = response.data.split(',');
        this.occurrences = Array(9).fill(0);
        for (let i = 0; i < this.numbers.length; i++) {
          let digit = parseInt(this.numbers[i]);
          this.occurrences[digit-1]++;
        }
      })
      .catch(error => {
        console.log(error);
      });
    },
  }

}
</script>

<style scoped lang="scss">
.graphic{
  height: 500px;
  width: 500px;
  margin: 0 auto;
  &-occurrences{
    height: 100%;
    tr{
      height: 100%;
      align-items: flex-end;
      display: flex;
      justify-content: center;
      td{
        background-color: blue;
        color:#fff;
        padding: 10px;
      }
    }
  }
  &-index{
    height: 20px;
    color: blue;
    font-weight: 800;
  }
}
</style>
