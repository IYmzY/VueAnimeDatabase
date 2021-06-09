<template>
  <div class="app">
    <header>
      <h1>The<strong>Anime</strong>database</h1>

      <form class="searchBox">
        <input
          type="search"
          class="searchField"
          placeholder="Search for an anime"
        />
      </form>
    </header>
  </div>
</template>

<script>
export default {};
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
  padding-top: 50px;
  padding-bottom: 50px;
  h1 {
    color: #888;
    font-size: 42px;
    font-weight: 400;
    text-align: center;
    text-transform: uppercase;
  }
  strong {
    color: #313131;
  }
  :hover {
    color: #313131;
  }
}
</style>
