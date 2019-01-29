<template>
  <div id="app">

    <b-navbar toggleable="md" type="dark" variant="dark" class="d-fixed">
      <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

      <b-navbar-brand href="/">My New Website</b-navbar-brand>

      <b-collapse is-nav id="nav_collapse">

        <!-- Right aligned nav items, collapsed on mobile -->
        <b-navbar-nav class="ml-auto">
          <b-nav-item-dropdown text="Projects" right>
            <b-dropdown-item href="/project/asd">PROJECT</b-dropdown-item>
            <b-dropdown-item href="/project/asd">PROJECT</b-dropdown-item>
          </b-nav-item-dropdown>
          <b-nav-item href="/about" right>About</b-nav-item>
        </b-navbar-nav>

      </b-collapse>
    </b-navbar>

    <!-- Dynamic Content -->
    <router-view />

  </div>
</template>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
