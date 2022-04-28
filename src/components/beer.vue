<template>
  <div class="beer__container">
     <div class="beer__card">
       <h2 class="beer__heading">Recommendation</h2>
       <div class="beer__description">
        <h3 class="beer__title">{{beer.name}} <span class="beer__brand">({{beer.brand}})</span></h3>
          <table class="beer__features-table">
            <caption class="beer__caption">{{beer.name}}{{beer.brand}}</caption>
            <tbody class="beer__table-body">
              <tr class="beer__table-row">
                <td class="beer__table-data">Style</td>
                <td class="beer__table-data">{{beer.style}}</td>  
              </tr>
              <tr class="beer__table-row">
                <td class="beer__table-data">Alcohol</td>
                <td class="beer__table-data">{{beer.alcohol}}</td>  
              </tr>
              <tr class="beer__table-row">
                <td class="beer__table-data">Hop</td>
                <td class="beer__table-data">{{beer.hop}}</td>  
              </tr>
              <tr class="beer__table-row">
                <td class="beer__table-data">Yeast</td>
                <td class="beer__table-data">{{beer.yeast}}</td>  
              </tr>
              <tr class="beer__table-row">
                <td class="beer__table-data">Malts</td>
                <td class="beer__table-data">{{beer.malts}}</td>  
              </tr>
              <tr class="beer__table-row">
                <td class="beer__table-data">ibu</td>
                <td class="beer__table-data">{{beer.ibu}}</td>  
              </tr>
              <tr class="beer__table-row">
                <td class="beer__table-data">blg</td>
                <td class="beer__table-data">{{beer.blg}}</td>  
              </tr>
            </tbody>
          </table>
        <button class="beer__button" v-on:click="fetchBeer">New recommendation!</button>
       </div>
     </div>
   </div>
</template>

<script>
export default {
  name: 'LoadBeer',
  data () {
    return {
      loading: false,
      beer: {}
    }
  },
  methods: {
    fetchBeer: function () {
        return fetch(`https://random-data-api.com/api/beer/random_beer`)
            .then(response => response.json())
            .then(json => this.beer = json)
    }
  },
  computed: {},
  mounted() {
    this.fetchBeer()
  }
}
</script>
