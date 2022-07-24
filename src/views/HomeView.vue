<template>
  <main v-if="!loading">
  <Data :text="title" :dataDate="dataDate" /> 
  <Boxes :stats="stats" />
<Country @get-country="getData" :countries="countries" />
</main>
  <main class="flex flex-col align-center justify-center text-center" v-else="loading">
  <div class="text-gray-500 text-3xl mt-10 mb-6">
    fetching data
  </div>
  </main>
</template>

<script>
import Data from '@/components/Data'
import Boxes from '@/components/Boxes'
import Country from '@/components/Country'


export default {
  name: 'HomeView',
  components: {Data,Boxes,Country},
  data(){
    return {
    loading: true ,
    title: 'global',
    dataDate : '',
    countries : [],
    stats : {} }
  },
  methods : {
async fetchData (){
const res = await fetch('https://api.covid19api.com/summary')
const data = await res.json()
return data

}

  ,
  getData(country){
    this.stats = country 
    this.title = country.Country
  },
  },
  async created(){
    
    const data = await this.fetchData()
    this.dataDate = data.Date 
    
    this.stats = data.Global 
    this.countries = data.Countries
    this.loading = false 
  }
    
}
</script>
