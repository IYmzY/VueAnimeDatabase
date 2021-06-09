<template>
  <div class="app">
    <header>
      <h1>
        The<strong>Anime</strong>database
      </h1>

      <form class="searchBox" @submit.prevent="handleSearch">
        <input
          type="search"
          class="searchField"
          placeholder="Search for an anime..."
          required
          v-model="searchQuery"
        />
      </form>
    </header>
    <main>
      <div class="cards">
        <card v-for="anime in animeList" :key="anime.mal_id" :anime="anime" />
      </div>
    </main>
  </div>
</template>

<script>
import { ref } from "vue";
import Card from "./components/Card.vue";
export default {
  components: { Card },
  setup() {
    const searchQuery = ref("");
    const animeList = ref([]);
    const handleSearch = async () => {
      animeList.value = await fetch(
        `https://api.jikan.moe/v3/search/anime?q=${searchQuery.value}`
      )
        .then((response) => response.json())
        .then((data) => data.results);
      console.log(animeList.value);
    };
    return {
      Card,
      searchQuery,
      animeList,
      handleSearch,
    };
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: fantasy;
}
a {
  text-decoration: none;
}
header {
  padding-top: 5%;
  padding-bottom: 5%;
  h1 {
    color: #afafaf;
    font-size: 10vw;
    font-weight: 400;
    text-align: center;
    text-transform: uppercase;
    margin-bottom: 80px;
  }
  strong {
    color: #313131;
  }
  :hover {
    color: #313131;
  }
  .searchBox {
    display: flex;
    justify-content: center;
    padding-left: 2%;
    padding-right: 2%;
    .searchField {
      appearance: none;
      background: none;
      border: none;
      outline: none;
      background-color: #f3f3f3;
      box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.15);
      display: block;
      width: 100%;
      height: 5vw;
      max-width: 78vw;
      padding-right: 50px;
      border-radius: 8px;
      font-size: 30px;
      padding-left: 2%;
      color: #313131;
      transition: 0.4s;
      &::placeholder {
        color: #afafaf;
      }
      &:focus,
      &:valid {
        color: #fff;
        background-color: #313131;
        box-shadow: 0px 0px 0px rgba(0, 0, 0, 0.15);
      }
    }
  }
}
main {
  max-width: 1200px;
  margin: 0 auto;
  padding-left: 2%;
  padding-right: 2%;

  .cards {
    display: flex;
    flex-flow: wrap;
    margin: 0 -8px;
  }
}
</style>
