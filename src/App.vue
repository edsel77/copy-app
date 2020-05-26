<template>
  <div id="app">
    <b-navbar toggleable="lg" type="dark" variant="info">
      <router-link to="/">
        <b-navbar-brand><strong>Copy App</strong></b-navbar-brand>
      </router-link>
    </b-navbar>
    <router-view></router-view>
  </div>
</template>

<script>

export default {
  data () {
    return {

    }
  },
  methods: {

  },
}
</script>

<style>

</style>
