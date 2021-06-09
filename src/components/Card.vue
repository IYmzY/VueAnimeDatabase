<template>
  <div class="card">
    <a href="#" target="_blank">
      <img src="https://place-hold.it/150x250" alt="Anime Poster Image" />
      <h3>{{ anime.title }}</h3>
    </a>
  </div>
</template>
<script>
export default {
  props: ["anime"],
};
</script>

<style lang="scss" scoped>
.card {
  flex: 1 1 33%;
  width: 33%;
  max-width: 33%;
  padding: 0px 16px;
  margin-bottom: 32px;
  img {
    widows: 100%;
    height: 300px;
    object-fit: cover;
    border-radius: 6%;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.15);
    transition: 0.4s;
  }
  h3 {
    display: block;
    padding: 16px;
    color: #313131;
    font-size: 1.8vw;
  }
  &:hover {
    img {
      transform: scale(1.05);
    }
    h3 {
      color: #f5853f;
    }
  }
}
</style>
