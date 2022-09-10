<template>
  <section class="cases pt140">
    <div class="container">
      <div class="row">
        <div class="col-12 col-lg-4 col-xl-5">
          <div class="cases__info">
            <div class="slogan">What we do?</div>
            <h2>Cases</h2>
            <h4 class="cases__text">
              We have experience as part of client's team and as an outsourcing
              subcontractor.
            </h4>
          </div>
        </div>
        <div class="col-12 col-lg-8 col-xl-7">
          <carousel
            class="cases__slider"
            :autoplay="false"
            :nav="false"
            :loop="true"
            :margin="0"
            :dots="false"
            :autoplay-speed="700"
            :items="1"
          >
            <div v-for="item in cases" :key="item.id" class="cases__slide">
              <div class="cases__item">
                <!-- <div class="cases__item-category">
                  <div class="label">Technology Stack</div>
                  <ul class="tag-list">
                    <li
                      v-for="(categoryItem, index) in item.category"
                      :key="index"
                    >
                      <span>{{ categoryItem }}</span>
                    </li>
                  </ul>
                </div> -->

                <h3 class="cases__item-name">
                  {{ item.title }}
                </h3>

                <div class="cases__item-product">
                  <div class="cases__item-product-logo">
                    <img
                      :src="
                        require(`~/assets/img/cases/` + item.productLogoUrl)
                      "
                      alt=""
                    />
                  </div>
                  <div class="cases__item-product-name">
                    {{ item.productName }}
                  </div>
                </div>

                <div class="cases__item-info">
                  <ul class="cases__item-info-list">
                    <li>
                      <div class="label">Service</div>
                      <p>
                        {{ item.service }}
                      </p>
                    </li>
                    <li>
                      <div class="label">Project stage</div>
                      <p>
                        {{ item.projectStage }}
                      </p>
                    </li>
                    <li>
                      <div class="label">Time to market</div>
                      <p>
                        {{ item.timeToMarket }}
                      </p>
                    </li>
                  </ul>
                </div>
                <div class="cases__item-description">
                  <div class="label">Project Description</div>
                  <div class="cases__item-description-text">
                    {{ item.description }}
                  </div>
                </div>
              </div>
            </div>
          </carousel>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      cases: [
        {
          id: 1,
          title:
            'Smart contract developing and integration WEB3 for SantaBeazzz',
          productLogoUrl: 'santa-beazzz.jpg',
          productName: 'Santa Beazzz',
          service:
            'Smart Contracts, Decentralized Application, Web3 Integration',
          projectStage: 'Report',
          timeToMarket: '2 weeks',
          description:
            'Santa Beazzz is a platform that has a collection of 10,000 NFTs. All Santa Beazzz NFTs are stored as ERC-721 tokens on the Polygon Blockchain and hosted on IPFS(Pinata). In this case, the BSAFE team considers the developing smart contract ERC721, generate collection and metadata, and integrate WEB3 to the landing page of the project.',
        },
        {
          id: 2,
          title: 'DAPP development for the DEXBeurop',
          productLogoUrl: 'bepr.png',
          productName: 'DEXBeurop',
          service:
            'Smart Contracts, Decentralized Application, Web3 Integration',
          projectStage: 'Report',
          timeToMarket: '2 weeks',
          description:
            'DEXBeurop is a decentralized open-source project which have their ecosystem and own token. There are 2 parts in the project: DeFi protocols and DAPP. The BSAFE team on first stage develop site and integrate WEB3. Second step was, to connect new liquidity pool of their token and make pricce chart for it.',
        },
        {
          id: 3,
          title: 'Cross-chain bridge development',
          productLogoUrl: 'bridge.png',
          productName: 'BSAFE Bridge',
          service:
            'Smart Contracts, Decentralized Application, Cross-chain bridges',
          projectStage: 'MVP',
          timeToMarket: '3 mounth',
          description:
            'BSAFE bridge it is decentalized app for cross chain swaps of tokens. Fewer and fewer people trust centralized exchangers. Therefore, the BSAFE team developed a bridge for transferring tokens to different blockchains (Polygon, Ethereum, BSC, TRON). Therefore, we implemented a number of non-standard solutions, which ensures a stable and safe operation of the migration service.',
        },
      ],
    };
  },
};
</script>

<style scoped lang="scss" src="./index.scss" />
