<template>
  <section class="faq pt140">
    <div class="container">
      <div class="slogan">Still have questions?</div>
      <h2>Read our FAQ</h2>
      <div class="faq__wrapper">
        <div
          v-for="(item, index) in faq"
          :key="index"
          class="faq__item"
          :class="{ active: item.visible }"
        >
          <div class="faq__item-question" @click="toggleItem(item)">
            <h5 class="question">{{ item.question }}</h5>
            <div class="faq__item-icons">
              <div v-if="!item.visible">+</div>
              <div v-else>-</div>
            </div>
          </div>
          <transition
            name="expand"
            mode="out-in"
            @enter="enter"
            @after-enter="afterEnter"
            @leave="leave"
          >
            <div v-if="item.visible" class="faq__item-content">
              <div class="faq__item-content-text">
                {{ item.content }}
              </div>
            </div>
          </transition>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      faq: [
        {
          visible: false,
          question: 'Do you provide Blockchain app development services?',
          content:
            'We develop Blockchain-based applications as well as integrate Blockchain technologies into existing apps.',
        },
        {
          visible: false,
          question: 'What Blockchain technologies do you apply?',
          content:
            'BSafe has extensive experience in working with many Blockchains technologies, including Bitcoin, Ethereum, Binance Smart Chain, Tron, Hyperledger and Solana.',
        },
        {
          visible: false,
          question: 'What type of Blockchain applications do you develop?',
          content:
            'We can develop or fork all existing decentralized applications like DEX, NFT marketplace, Bridge and multi-signature wallet.',
        },
        {
          visible: false,
          question:
            'Do you provide Blockchain solutions for existing businesses?',
          content:
            'Yes, we do. Our BSafe Blockchain team develop complex solutions for existing businesses.',
        },
      ],
    };
  },
  methods: {
    toggleItem(item) {
      this.faq.forEach((i) => {
        if (i !== item) {
          i.visible = false;
        } else {
          item.visible = !item.visible;
        }
      });
    },
    enter(element) {
      const width = getComputedStyle(element).width;
      element.style.width = width;
      element.style.position = 'absolute';
      element.style.visibility = 'hidden';
      element.style.height = 'auto';
      const height = getComputedStyle(element).height;
      element.style.width = null;
      element.style.position = null;
      element.style.visibility = null;
      element.style.height = 0;
      // getComputedStyle(element).height;
      requestAnimationFrame(() => {
        element.style.height = height;
      });
    },
    afterEnter(element) {
      element.style.height = 'auto';
    },
    leave(element) {
      const height = getComputedStyle(element).height;
      element.style.height = height;
      // getComputedStyle(element).height;
      requestAnimationFrame(() => {
        element.style.height = 0;
      });
    },
  },
};
</script>

<style scoped lang="scss" src="./index.scss" />
