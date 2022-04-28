<template>
  <div id="app" class="hero">
    <section class="user">
      <user/>
    </section>
    <section class="beer">
      <beer/>
    </section>
  </div>
</template>

<script>

import user from './components/user'
import beer from './components/beer'

export default {
  name: 'App',
  components: {
    user,
    beer
  }
}
</script>

<style lang="scss">
  @import "./assets/style";
  .hero {
    padding: 20px;
    padding-top: 80px;
    display: flex;
    align-items: center;
    justify-content: center;
      @media (max-width: 768px) {
        padding-top: 20px;
        flex-wrap: wrap;
     }
  }
</style>
