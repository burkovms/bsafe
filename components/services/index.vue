<template>
  <div class="services pt140">
    <section
      class="services__cover pb140"
      :style="{
        backgroundImage: `url(${require('@/assets/img/bg-services.svg')})`,
      }"
    >
      <div class="container">
        <div class="slogan">What we do?</div>
        <h2>Our Services</h2>
        <div class="services__row row">
          <div
            v-for="item in services"
            :key="item.id"
            class="services__col col-12 col-md-6 col-lg-4"
          >
            <div class="services__item">
              <div class="services__item-icon">
                <img
                  :src="require(`~/assets/img/services/service-` + item.img)"
                  alt=""
                />
              </div>
              <h6 class="services__item-name">{{ item.name }}</h6>
              <ul class="services__item-list secondary">
                <li v-for="(itemList, index) in item.list" :key="index">
                  {{ itemList }}
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      services: [
        {
          id: 1,
          img: '1.svg',
          name: 'Blockchain Ecosystem',
          list: [
            'Cryptocurrencies from scratch',
            'Blockchain forks',
            'Blockchain based platforms',
            'Blockchain nodes',
            'Cross-chain bridges',
          ],
        },
        {
          id: 2,
          img: '2.svg',
          name: 'Decentralized Application',
          list: [
            'DeFi applications',
            'Decentralized exchanges',
            'DAO - Decentralized autonomous organization',
            'Staking platforms',
            'Crypto wallets',
            'Crypto games',
          ],
        },
        {
          id: 3,
          img: '3.svg',
          name: 'Smart Contracts',
          list: [
            'Smart contracts',
            'Stablecoin development',
            'Security audits',
            'Token emission and distribution',
          ],
        },
        {
          id: 4,
          img: '1.svg',
          name: 'Developer Tools',
          list: ['SDKs', 'APIs', 'Online/Offline IDEs', 'Plugins'],
        },
        {
          id: 5,
          img: '1.svg',
          name: 'Enterprise Solution',
          list: [
            'Governance (voting) systems',
            'Logistics solutions',
            'Supply chains',
            'Compliance system',
          ],
        },
        {
          id: 6,
          img: '1.svg',
          name: 'Blockchain Integration',
          list: [
            'Centralized exchange',
            'Blockchain based micropayment services',
            'Decentralized marketplaces',
            'CRM/ERP blockchain integration',
          ],
        },
      ],
    };
  },
};
</script>

<style scoped lang="scss" src="./index.scss" />
