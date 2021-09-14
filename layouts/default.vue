<template>
  <div>
    <nav>
      <ul>
        <li><NuxtLink to="/">Home</NuxtLink></li>
        <li><NuxtLink to="/fade">Fade</NuxtLink></li>
        <li><NuxtLink to="/bounce">Bounce</NuxtLink></li>
      </ul>
    </nav>
    <main>
      <img
        src="https://image.shutterstock.com/image-photo/suraj-mukhi-flower-my-great-260nw-1467178388.jpg"
      />
      <Nuxt />
    </main>
  </div>
</template>

<style scoped>
.nav-bar {
  display: flex;
}
</style>