<template>
  <nav>
    <div class="container">
        <div class="grid">
          <div class="column-xs-12 column-md-10">
              <p id="highlight">SHIBA GALLERY</p>
          </div>
        </div>
      </div>
  </nav>
  <BodyComponent />
  <footer>
    <div class="container">
      <div class="grid">
        <div class="column-xs-12">
          <p class="copyright">&copy; Copyright 2022 - IT810</p>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
  import BodyComponent from './components/BodyComponent.vue'

  export default{
    name: 'App',
    components: {
      BodyComponent
    }
  }
</script>

<style lang="scss">

  $white: #fff;
  $black: #2e2e2e;
  $gray: #787878;
  $highlight: #ea8478;
  $footer: #f7f7f7;

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    &::before, &::after {
      box-sizing: border-box;
    }
  }

  body {
    font-family: 'Barlow', sans-serif;
    font-size: 1.125rem;
    line-height: 1.5;
    color: $gray;
    background: $white;
    text-rendering: optimizeLegibility;
  }

  ul li {
    margin: 0 1.5rem 0 0;
  }

  a {
    color: $gray;
    text-decoration: none;
    transition: all 0.2s ease;
    &:hover {
      color: $black;
    }
    &.active {
      color: $black;
    }
  }

  nav {
    padding: 2rem 0;
    background-color: aliceblue;
    margin-bottom: 50px;

    ul {
      display: flex;
      justify-content: flex-start;
    }
    li {
      font-size: 1.25rem;
      &:nth-child(2) {
        margin: 0;
      }
    }
  }

  #highlight {
    color: $highlight;
    font-size: 1.25rem;
  }

  footer {
    margin-top: 50px;
    padding: 2rem 0;
    background: #f7f7f7;
    text-align: center;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
</style>
