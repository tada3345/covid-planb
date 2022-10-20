<template>
  <div class="grid md:grid-cols-2 gap-4">
    <!-- Box 1 -->
    <div class="shadow-md bg-blue-100 p-10 text-center rounded">
      <h3 class="text-3xl text-gray-900 font-bold mb-4">陽性者数</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">昨日:</span>
        {{ numberWithCommas(stats.NewConfirmed) }}
        件
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">合計:</span>
        {{ numberWithCommas(stats.TotalConfirmed) }}
        件
      </div>
    </div>
    <!-- Box 2 -->
    <div class="shadow-md bg-blue-200 p-10 text-center rounded">
      <h3 class="text-3xl text-gray-900 font-bold mb-4">死亡者数</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">昨日:</span>
        {{ numberWithCommas(stats.NewDeaths) }}
        件
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">合計:</span>
        {{ numberWithCommas(stats.TotalDeaths) }}
        件
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DataBoxes',
  props: ['stats'],
  methods: {
    numberWithCommas(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
    },
  },
};
</script>
