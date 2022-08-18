<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate"/>
  <DataBoxes :stat="stat"/>
    <CountrySelect :countries="countries" @get-country="getCountryData" />
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Fetching Data
    </div>
    <img class="w-24 m-auto" :src="loadingImage" alt=""/>
  </main>
</template>

<script>
// @ is an alias to /src
import DataTitle from '@/components/DataTitle'
import DataBoxes from "@/components/DataBoxes";
import CountrySelect from "@/components/CountrySelect";

export default {
  name: 'HomeView',
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect
  },
  data(){
      return{
        loading:true,
        title: 'Global',
        dataDate: '',
        stat:{},
        countries:[],
        loadingImage: require('../assets/hourglass.gif')
      }
       },
  methods:{
    async fetchCovidData(){
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    },
     getCountryData(country){
      this.stat= country
      this.title = country.Country
    }
  },
  async created(){
   const data = await this.fetchCovidData()

   this.dataDate = data.Date
   this.stat = data.Global
   this.countries = data.Countries
    this.loading = false
  }
}
</script>
