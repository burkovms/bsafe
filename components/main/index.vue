<template>
  <section
    class="main pt140 pb140"
    :style="{
      backgroundImage: `url(${require('@/assets/img/main-bg-gradient.png')})`,
    }"
  >
    <div class="container-fluid">
      <h1>We Build Blockchain Ecosystem</h1>
      <p class="main__slogan">
        Great tech can solve the unsolvable. It can make our lives easier and
        more enjoyable. And it can change the world for the better
      </p>
      <a href="#contact" class="btn" @click.prevent="scrollAnchor()">
        <span>Estimate my project</span>
      </a>
    </div>

    <Technology />
  </section>
</template>

<script>
export default {
  methods: {
    scrollAnchor() {
      const element = document.getElementById('contact');
      const y = element.getBoundingClientRect().top + window.pageYOffset - 0;
      window.scrollTo({ top: y, behavior: 'smooth' });
    },
  },
};
</script>

<style scoped lang="scss" src="./index.scss" />
