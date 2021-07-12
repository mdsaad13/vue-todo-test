<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-light bg-light mb-5">
      <router-link :to="{ name: 'Home' }" class="navbar-brand font-weight-bold"
        >Vue app</router-link
      >
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item">
            <router-link :to="{ name: 'Home' }" class="nav-link" exact
              >Home</router-link
            >
          </li>
          <li class="nav-item">
            <router-link :to="{ name: 'About' }" class="nav-link" exact
              >About</router-link
            >
          </li>
          <li class="nav-item">
            <router-link :to="{ name: 'Todo' }" class="nav-link" exact
              >Todo</router-link
            >
          </li>
        </ul>
      </div>
    </nav>
    <div class="container-fluid">
      <transition name="fade" mode="out-in">
        <router-view />
      </transition>
    </div>
  </div>
</template>

<style lang="scss">
.navbar .router-link-active:not(.navbar-brand) {
  color: var(--primary) !important;
}

.navbar-light .navbar-nav .nav-link {
  font-weight: bold;
}

.fade-enter-active,
.fade-leave-active {
  transition-duration: 0.3s;
  transition-property: height, opacity;
  transition-timing-function: ease;
  overflow: hidden;
}

.fade-enter,
.fade-leave-active {
  opacity: 0;
}
</style>
