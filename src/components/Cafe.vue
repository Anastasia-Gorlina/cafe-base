<template>
  <div class="Cafe">
    <div v-if="!loading" class="info">
      <div>Name: {{ name }}</div>
      <div>Address: {{ address }}</div>
      <div>Landmark: {{ landmark }}</div>
      <div>Cuisine: {{ cuisine }}</div>
      <div>Distance: {{ distance }}</div>
      <div>Time: {{ time }}</div>
      <div>Photo: {{ photo }}</div>
      <div>Time: {{ time }}</div>
      <div>Photo: {{ photo }}</div>
      <div>Business_lunch: {{ business_lunch }}</div>
      <div>Price: {{ price }}</div>
    </div>
    <div v-else>Loading...</div>
    <button @click="displayData()" class="cafe-base">---</button>
  </div>
</template>

<script>
export default {
  name: "Cafe",

  data() {
    return {
      name: true,
      address: null,
      landmark: null,
      cuisine: null,
      distance: null,
      time: null,
      photo: null,
      buisness_lunch: null,
      price: null,
    };
  },

  methods: {
    async getRandomBeer() {
    this.name = true;

    return fetch('<https://bandaumnikov.ru/api/test/site/get-index>').then(
        (response) => response.json()
      );
    },
    displayData() {
      this.getRandomBeer().then((cafeData) => {
        this.name = cafeData.name;
        this.address = cafeData.address;
        this.landmark = cafeData.landmark;
        this.cuisine = cafeData.cuisine;
        this.distance = cafeData.distance;
        this.time = cafeData.time;
        this.photo = cafeData.photo;
        this.buisness_lunch = cafeData.buisness_lunch;
        this.price = cafeData.price;

        this.loading = false;
      });
    },
  },

  created() {
    this.displayData();
  },
};
</script>

<style>
.cafe {
  width: 300px;
}

.cafe-base {
  margin-top: 20px;
  width: 100px;
  height: 30px;
  background-color: white;
  border: 1px solid black;
}
</style>