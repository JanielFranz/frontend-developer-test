<script>
import { Country } from "../model/country.entity.js";
import CountryItemDialog from "./country-item-dialog.component.vue";

export default {
  name: "country-card-item",
  components: { CountryItemDialog },
  props: {
    country: {
      type: Country,
      required: true
    }
  },
  data() {
    return {
      dialogVisible: false
    }
  },
  methods: {
    openDialog() {
      this.dialogVisible = true;
    },
    closeDialog() {
      console.log('close dialog');
      this.dialogVisible = false;
    }
  }
}
</script>

<template>
  <div class="card-container" @click="openDialog">
    <pv-card style="overflow:hidden" class="card ml-3 mb-4">
      <template #header>
        <img :src="country.countryImgUrl" alt="country image" class="country-img">
      </template>
      <template #title>
        <div class="country-info-container flex align-items-center flex-wrap">
          <img :src="country.countryFlagImgUrl"
               :alt="country.countryFlagImgUrl"
               class="country-flag" />
          <div class="country-text-container">
            <h3 class="title-center">{{ country.name }}</h3>
            <h4 class="subtitle-center">{{ country.continent }}</h4>
          </div>
        </div>
      </template>
    </pv-card>
  </div>

  <country-item-dialog :country="country" :visible="dialogVisible" v-on:close-selected="closeDialog"/>
</template>

<style scoped>
.country-text-container {
  text-align: left;
  width: 65%;
}

.title-center {
  font-size: 1.5rem;
  font-weight: bold;
  margin: 0;
  color: deepskyblue;
}

.subtitle-center {
  margin-top: 0.1rem;
  font-size: 0.9rem;
  color: #808080;
}

.country-flag {
  width: 4rem;
  height: 2rem;
  margin-right: 0.5rem;
  margin-bottom: 1rem;
}

.country-img {
  width: 19rem;
  height: 8rem;
}


.card{
  cursor: pointer;
  width: 19rem;
  height:14rem;
  background-color: white;
}

.card:hover {
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  transition: 0.3s;
  background-color: deepskyblue ;
  h3 {
    color: white;
  }
}

/* Responsiveness for small screens */
@media (max-width: 768px) {
  .card {
    width: 100%;
    height: auto;
    margin-left: 0;
    margin-right: 0;
  }
  .country-img {
    width: 100%;
    height: auto;
  }
  .country-info-container {
    flex-direction: column;
    align-items: center;
  }
  .country-flag {
    width: 4rem;
    height: 2.5rem;
    margin-bottom: 0.5rem;
  }
  .country-text-container {
    width: 100%;
    text-align: center;
  }
  .title-center {
    font-size: 1.2rem;
  }
  .subtitle-center {
    font-size: 0.8rem;
  }
}

@media (max-width: 576px) {
  .card {
    width: 95%;
    height: 23rem;
    margin-left: 0;
    margin-right: 0;
  }
  .card-container{
    width: 90%;
    height: 23rem;
  }
  .country-img {
    width: 100%;
    height: auto;
  }
  .country-info-container {
    flex-direction: column;
    align-items: center;
  }
  .country-flag {
    width: 3rem;
    height: 2rem;
    margin-bottom: 0.5rem;
  }
  .country-text-container {
    width: 100%;
    text-align: center;
  }
  .title-center {
    font-size: 2rem;
  }
  .subtitle-center {
    font-size: 1.4rem;
  }
}
</style>
