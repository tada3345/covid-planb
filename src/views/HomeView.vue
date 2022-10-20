<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />

    <DataBoxes :stats="stats" />
    <CountrySelect @get-country="getCountryData" :countries="countries" />
    <button
      @click="clearCountryData"
      v-if="stats.Country"
      class="block bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600 float-right md:block md:w-100"
    >
      全世界に戻る
    </button>
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">少々お待ちください</div>
    <img :src="loadingImage" alt="少々お待ちください" class="w-24 m-auto" />
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle';
import DataBoxes from '@/components/DataBoxes';
import CountrySelect from '@/components/CountrySelect';

export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
  },
  data() {
    return {
      loading: true,
      title: '全世界',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/hourglass.gif'),
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch('https://api.covid19api.com/summary');
      // const res = await fetch('../components/api/api.json');
      return await res.json();
    },
    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },
    async clearCountryData() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = '世界の統計';
      this.stats = data.Global;
      this.loading = false;
    },
  },
  async created() {
    try {
      const data = await this.fetchCovidData();
      // this.dataDate = data.Date;
      this.dataDate = new Date().toISOString();
      this.stats = data.Global;
      this.countries = data.Countries;
      this.loading = false;
    } catch (err) {
      console.err(err);
    }
  },
};
</script>
