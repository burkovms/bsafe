<template>
  <section class="technology">
    <div class="container">
      <carousel
        class="technology-slider"
        :items="5"
        :autoplay="false"
        :nav="false"
        :loop="false"
        :dots="false"
        :margin="16"
        :autoplay-speed="2000"
        autoplay-timeout="3500"
        :responsive="{
          0: { items: 2, loop: true, autoplay: true },
          576: { items: 3, loop: true, autoplay: true },
          768: { items: 4, loop: true, autoplay: true },
          992: { loop: false },
        }"
      >
        <div
          v-for="(item, index) in technology"
          :key="index"
          class="technology__slide"
        >
          <img
            :src="require(`~/assets/img/technology/technology-` + item.url)"
            :alt="item.name"
          />
        </div>
      </carousel>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      technology: [
        {
          name: 'solana',
          url: 'solana.svg',
        },
        {
          name: 'polkadot',
          url: 'polkadot.svg',
        },
        {
          name: 'avalanche',
          url: 'avalanche.svg',
        },
        {
          name: 'ethereum',
          url: 'ethereum.svg',
        },
        {
          name: 'binance smart chain',
          url: 'binance-smart-chain.svg',
        },
      ],
    };
  },
};
</script>

<style scoped lang="scss" src="./index.scss" />
