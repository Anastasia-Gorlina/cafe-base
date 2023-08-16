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
      <div>Buisness_lunch: {{ business_lunch }}</div>
      <div>Price: {{ price }}</div>
    </div>
    <div v-else>Загрузка</div>
    <button @click="displayData()" class="roll-cafe">Выбрать кафе</button>
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
      business_lunch: null,
      price: null,
    };
  },

  methods: {
    getItems() {
      fetch('<https://example.com/api/cafe>')
        .then(response => response.json())
        .then(displayData => {
          this.items = displayData; 
        })
        .catch(error => console.error(error));
    },
    displayData() {
      this.getRandomCafe().then((cafeData) => {
        this.name = cafeData.name;
        this.address = cafeData.address;
        this.landmark = cafeData.landmark;
        this.cuisine = cafeData.cuisine;
        this.distance = cafeData.distance;
        this.time = cafeData.time;
        this.photo = cafeData.photo;
        this.business_lunch = cafeData.business_lunch;
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

.roll-cafe {
  margin-top: 20px;
  width: 100px;
  height: 30px;
  background-color: white;
  border: 1px solid black;
}
button:hover {
    cursor: pointer;
}
</style>
