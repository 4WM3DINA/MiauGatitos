<template>
  <div id="app" class="container">
    <div class="row">
      <h1 class="col-12 text-center text-info">RANDOM GIF CAT</h1>
      <div class="col-12">
        <div class="mb-3">
          <label class="form-label fs-5">Título</label>
          <input type="text" class="form-control" v-model="myTitle" />
        </div>
        <div class="mb-3">
          <label class="form-label fs-5">Filtro</label>
          <select class="form-select" v-model="myFilter">
            <option v-for="(item, i) in filters" :key="i" :value="item">
              {{ item }}
            </option>
          </select>
        </div>
        <div class="mb-3">
          <div>
            <label class="form-label fs-5">Color</label>
            <select class="form-select" v-model="myColor">
              <option v-for="(item, i) in colors" :key="i" :value="item">
                {{ item }}
              </option>
            </select>
            <div
              class="colorsito"
              :style="{ 'background-color': getColor }"
            ></div>
          </div>
        </div>
        <div class="mb-3">
          <label class="form-label fs-5">Tamaño</label>
          <input type="number" class="form-control" v-model="mySize" />
        </div>
        <button class="btn btn-primary" @click="clicked()">
          Obtener gatito
        </button>
      </div>
      <div class="col-12">
        <img :src="myCat" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  computed: {
    getColor() {
      return this.myColor;
    },
  },
  data() {
    return {
      filters: ["blur", "mono", "sepia", "negative", "paint", "pixel"],
      colors: ["green", "red", "orange", "white", "yellow", "purple", "brown"],
      myCat: "",
      myFilter: "",
      myColor: "",
      myTitle: "",
      mySize: "",
    };
  },
  methods: {
    async getKittins(titulo, filtro, color, tamaño) {
      try {
        const req = await fetch(
          `https://cataas.com/cat/gif/says/${titulo}?filter=${filtro}&color=${color}&size=${tamaño}&type=or`
        );
        this.myCat = req.url;
        console.log(req.url);
      } catch (error) {
        this.myCat =
          "https://www.meme-arsenal.com/memes/c9e6371faa3b57eaee1d35595ca8e910.jpg";
        console.log(error);
      }
    },
    clicked() {
      this.getKittins(this.myTitle, this.myFilter, this.myColor, this.mySize);
    },
  },
};
</script>

<style>
.colorsito {
  width: 38px;
  height: 38px;
  border: 4px solid rgba(56, 215, 226, 0.753);
  border-radius: 50% 50%;
  margin: 0 auto;
  margin-top: 1em;
}
.row {
  background-color: rgba(155, 106, 106, 0.699);
}
button.btn.btn-primary {
  background-color: rgba(173, 20, 135, 0.603);
  border: 3px solid rgba(241, 11, 42, 0.603);
  color: #f9f9fa;
  font-size: 1.3rem;
}
.col-12 {
  padding: 1em;
}
</style>
