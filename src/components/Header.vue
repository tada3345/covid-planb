<template>
  <header class="text-center bg-gray-500 text-white p-4 mb-10">
    <div class="top_img mb-4 p-4"></div>
    <div class="text-3xl md:text-5xl font-bold mb-3">
      <i class="fa fa-viruses"></i> Covid-19 世界情報　
    </div>

    <p>
      <!-- API by -->
      <a
        class="text-blue-300"
        href="https://covid19api.com"
        target="_blank"
      ></a>
    </p>
  </header>
</template>

<script>
export default {
  name: 'Header',
};
</script>

<style>
.top_img {
  background-image: url('https://images.unsplash.com/photo-1584931423298-c576fda54bd2?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80');
  height: 180px;
  width: 100%;
  margin: 0;
  padding: 0;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
</style>
