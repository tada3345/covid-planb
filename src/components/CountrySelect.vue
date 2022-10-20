<template>
  <select
    @change="onChange()"
    v-model="selected"
    class="form-select my-10 block w-full border border-sky-400 p-3 rounded"
  >
    <option value="0">国を選択してください</option>
    <option v-for="country in countries" :value="country.ID">
      {{ country.Country }}
    </option>
  </select>
</template>

<script>
export default {
  name: 'CountrySelect',
  props: ['countries'],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find((item) => item.ID === this.selected);
      console.log(country);
      this.$emit('get-country', country);
    },
  },
};
</script>
