<template>
  <div class="cards">
    <div :key="item.id" v-for="item in data" class="card" @mouseenter="startAnime(item)" @mouseleave="endAnime(item)">
      <div class="hero">
        <img class="hero-image" :src="item.image" :alt="item.title">
        <h1>{{ item.title }}</h1>
        <div class="hero-content">
          <h2 v-show="item.toggleText">{{ item.subtitle }}</h2>
          <div class="stars">
            <Icon icon="teenyicons:star-solid" width="30" height="30" style="color: #ef0b0b" />
            <Icon icon="teenyicons:star-solid" width="30" height="30" style="color: #ef0b0b" />
            <Icon icon="teenyicons:star-solid" width="30" height="30" style="color: #ef0b0b" />
            <Icon icon="teenyicons:star-solid" width="30" height="30" style="color: #ef0b0b" />
            <Icon icon="teenyicons:star-solid" width="30" height="30" style="color: #ef0b0b" />
          </div>
        </div>
      </div>
      <h2 v-show="!item.toggleText" class="nav-text">{{ item.subtitle }}</h2>
      <div class="nav">
        <p>details</p>
        <p>memories</p>
      </div>
    </div>
  </div>
  <h1 class="header">Let’s get Lost</h1>
</template>

<script>
import { Icon } from '@iconify/vue';


export default {
  name: 'App',
  components: {
    Icon
  },
  data() {
    return {
      data: [
        { id: 1, title: "Breakfast", subtitle: "Hot cup of coffee", ratings: 5, image: "./assets/benaja-germann.jpg", toggleText: true },
        { id: 2, title: "Meat Lover", subtitle: "Somked ribs", ratings: 5, image: "./assets/negley-stockman.jpg", toggleText: true },
        { id: 3, title: "Tea", subtitle: "Oolong tea", ratings: 5, image: "./assets/okeykat.jpg", toggleText: true },
        { id: 4, title: "Bread", subtitle: "Baguette breakfast", ratings: 5, image: "./assets/phoebe-lynch.jpg", toggleText: true },
      ],
    }
  },
  methods: {
    startAnime(item) {
      item.toggleText = !item.toggleText
    },
    endAnime(item) {
      item.toggleText = !item.toggleText
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #444;
  margin-top: 60px;
  width: 100%;
}

.header {
  font-size: 12rem;
  width: 90%;
  margin: 0 auto;
}

.cards {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  gap: 2rem;

  width: 90%;
  margin: 0 auto;
}

.card {
  width: 30rem;
}

.hero {
  width: 100%;
  height: 46rem;
  border-radius: 1rem;
  background-size: cover;
  background-repeat: no-repeat;
  text-align: center;

  display: flex;
  flex-direction: column;
  justify-content: space-between;

  padding-top: 5px;
  padding-bottom: 1rem;

  background-color: rgba(0, 0, 0, 0.4);
  position: relative;
  overflow: hidden;

  color: #fff;
}

.hero-image {
  position: absolute;
  z-index: -1;

  width: 100%;
  height: 100%;
}

.nav {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
}

.hero-content h2 {
  transition: display 2s linear 1s;
}

.nav-text {
  text-align: center;
  transition: display 2s linear 1s;
}
</style>
