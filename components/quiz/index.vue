<template>
  <section class="quiz">
    <div class="container">
      <form
        action="/"
        class="quiz__wrap"
        method="post"
        @submit.prevent="formSubmit"
      >
        <div v-if="currentStep == 0" class="quiz__start quiz__step step-0">
          <div class="quiz__start-top">
            <img class="quiz__start-img" src="@/static/roket.svg" alt="roket" />
          </div>
          <div class="quiz__start-body">
            <h1 class="title-gradient-border" data-title="Quiz Name">
              Quiz Name
            </h1>
            <h4 class="quiz-slogan">
              An advanced approach for your blockchain app.
            </h4>
            <p class="quiz-text secondary">
              Go from concept to MVP in 90 days or less.
            </p>
          </div>
          <div class="quiz__start-bottom">
            <button class="btn btn-round" @click.prevent="goToStep(1)">
              <span>GO!</span>
            </button>
          </div>
        </div>

        <div v-if="currentStep == 1" class="quiz__step step-1">
          <div class="quiz__step-row row">
            <div class="col-12 col-lg-6 quiz__step-col">
              <div class="step-count secondary"><span>01</span> / 04</div>
              <h3 class="text-border step-title">A little bit of detail.</h3>
              <h3 class="step-slogan">
                Tell us in which domain area your project is located.
              </h3>
              <p class="quiz-text secondary">Select one or more options</p>
            </div>
            <div class="col-12 col-lg-6 quiz__step-col">
              <div class="quiz__toggle">
                <div
                  v-for="item in step1"
                  :key="item.id"
                  class="quiz__toggle-item"
                  :class="{ active: item.visible }"
                >
                  <div
                    class="quiz__toggle-item-name"
                    @click="item.visible = !item.visible"
                  >
                    <span class="name">{{ item.name }}</span>
                    <span
                      v-if="item.list.filter((item) => item.checked).length > 0"
                      class="item-length"
                    >
                      {{ item.list.filter((item) => item.checked).length }}
                    </span>
                  </div>
                  <div class="quiz__toggle-item-content">
                    <ul class="tag-list">
                      <li v-for="tag in item.list" :key="tag.id">
                        <div class="checkbox-group">
                          <input
                            v-model="tag.checked"
                            type="checkbox"
                            :name="tag.name"
                          />
                          <span>{{ tag.value }}</span>
                        </div>
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="quiz__step-buttons">
            <button
              class="btn btn-gray"
              type="button"
              @click.prevent="goToStep(0)"
            >
              <SvgIcon name="arrow-left" width="13" height="10" />
              <span>Prev</span>
            </button>
            <button class="btn" type="button" @click.prevent="goToStep(2)">
              <span>Next</span>
              <SvgIcon name="arrow-right" width="13" height="10" />
            </button>
          </div>
        </div>

        <div v-if="currentStep == 2" class="quiz__step step-2">
          <div class="quiz__step-row row">
            <div class="col-12 col-lg-6 quiz__step-col">
              <div class="step-count secondary"><span>02</span> / 04</div>
              <h3 class="text-border step-title">A little bit of detail.</h3>
              <h3 class="step-slogan">
                Tell us what technologies do you need in your project.
              </h3>
              <p class="quiz-text secondary">Select one or more options</p>
            </div>
            <div class="col-12 col-lg-6 quiz__step-col">
              <div class="quiz__toggle">
                <div
                  v-for="item in step2"
                  :key="item.id"
                  class="quiz__toggle-item"
                  :class="{ active: item.visible }"
                >
                  <div
                    class="quiz__toggle-item-name"
                    @click="item.visible = !item.visible"
                  >
                    <span class="name">{{ item.name }}</span>
                    <span
                      v-if="item.list.filter((item) => item.checked).length > 0"
                      class="item-length"
                    >
                      {{ item.list.filter((item) => item.checked).length }}
                    </span>
                  </div>
                  <div class="quiz__toggle-item-content">
                    <ul class="tag-list">
                      <li v-for="tag in item.list" :key="tag.id">
                        <div class="checkbox-group">
                          <input
                            v-model="tag.checked"
                            type="checkbox"
                            :name="tag.name"
                          />
                          <span>{{ tag.value }}</span>
                        </div>
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="quiz__step-buttons">
            <button
              class="btn btn-gray"
              type="button"
              @click.prevent="goToStep(1)"
            >
              <SvgIcon name="arrow-left" width="13" height="10" />
              <span>Prev</span>
            </button>
            <button class="btn" type="button" @click.prevent="goToStep(3)">
              <span>Next</span>
              <SvgIcon name="arrow-right" width="13" height="10" />
            </button>
          </div>
        </div>

        <div
          v-if="currentStep == 3"
          class="quiz__step-period quiz__step step-3"
        >
          <div class="quiz__step-row row">
            <div class="col-12 col-md-6">
              <div class="step-count secondary"><span>03</span> / 04</div>
              <h3 class="text-border step-title">A little bit of detail.</h3>
              <h3 class="step-slogan">
                How many time you have for developing of MVP?
              </h3>
            </div>
            <div class="col-12 col-md-6">
              <div class="quiz__step-period-content">
                <div class="quiz__step-period-input">
                  <input
                    v-model="value"
                    class="input-range"
                    type="range"
                    min="0"
                    :max="step3.length - 1"
                    step="1"
                    :style="{ backgroundSize: backgroundSize }"
                    @input="updateSlider"
                  />
                </div>
                <ul class="quiz__step-period-list">
                  <li
                    v-for="(item, index) in step3"
                    :key="index"
                    :class="{ active: value == index }"
                    @click="updateValue(index)"
                  >
                    <span class="link">{{ item }}</span>
                  </li>
                </ul>
              </div>
            </div>
          </div>
          <div class="quiz__step-buttons">
            <button
              class="btn btn-gray"
              type="button"
              @click.prevent="goToStep(2)"
            >
              <SvgIcon name="arrow-left" width="13" height="10" />
              <span>Prev</span>
            </button>
            <button class="btn" type="button" @click.prevent="goToStep(4)">
              <span>Next</span>
              <SvgIcon name="arrow-right" width="13" height="10" />
            </button>
          </div>
        </div>

        <div v-if="currentStep == 4" class="quiz__step step-4">
          <div class="quiz__step-row row">
            <div class="col-12 col-lg-6 quiz__step-col">
              <div class="step-count secondary"><span>04</span> / 04</div>
              <h3 class="text-border step-title">A little bit of detail.</h3>
              <h3 class="step-slogan">
                Enter your personal details and tell us about the project.
              </h3>
              <p class="quiz-text secondary">Or add a presentation</p>
            </div>
            <div class="col-12 col-lg-6 quiz__step-col">
              <div class="form">
                <ul class="contact__form-list-input">
                  <li>
                    <div class="label">Your Full Name</div>
                    <input
                      v-model.trim="step4.name"
                      type="text"
                      name="your-name"
                      :class="{
                        error: $v.step4.name.$error,
                      }"
                      @input="$v.step4.name.$touch()"
                    />
                    <div v-if="$v.step4.name.$error" class="input-help">
                      <span v-if="!$v.step4.name.required">
                        Name cannot be blank.
                      </span>
                    </div>
                  </li>
                  <li>
                    <div class="label">Email Adress</div>
                    <input
                      v-model.trim="step4.email"
                      type="email"
                      name="your-email"
                      :class="{
                        error: $v.step4.email.$error,
                      }"
                      @input="$v.step4.email.$touch()"
                    />
                    <div v-if="$v.step4.email.$error" class="input-help">
                      <span v-if="!$v.step4.email.required">
                        E-mail cannot be blank.
                      </span>
                    </div>
                  </li>
                  <li>
                    <div class="label">Description (optional)</div>
                    <textarea
                      v-model.trim="step4.description"
                      name="your-description"
                      placeholder="Write here what you think is important about your project"
                      maxlength="250"
                    ></textarea>
                  </li>
                  <li>
                    <div class="label">Upload Files (optional)</div>
                    <div class="input-file">
                      <div v-if="!step4.files" class="upload">
                        <p>Drag files here to upload</p>
                        <span class="btn">
                          <input
                            multiple
                            type="file"
                            name="your-file"
                            accept=".pdf,.txt,.jpeg,.jpg"
                            @change="onFileChanged"
                          />
                          <SvgIcon name="upload" width="17" height="16" />
                          <span>Or choose file</span>
                        </span>
                      </div>
                      <div v-else class="uploaded">
                        <ul class="tag-list">
                          <li v-for="(file, index) in step4.files" :key="index">
                            <span>{{ file.name }}</span>
                          </li>
                        </ul>
                        <button class="btn" @click="resetInputFiles">
                          <SvgIcon name="reset" width="17" height="17" />
                          <span>Reset Files</span>
                        </button>
                      </div>
                    </div>
                  </li>
                </ul>
              </div>
            </div>
          </div>
          <div class="quiz__step-buttons">
            <button
              class="btn btn-gray"
              type="button"
              @click.prevent="goToStep(3)"
            >
              <SvgIcon name="arrow-left" width="13" height="10" />
              <span>Prev</span>
            </button>
            <button type="submit" class="btn">
              <span>Submit</span>
            </button>
          </div>
        </div>

        <div v-if="currentStep == 5" class="quiz__finish quiz__step step-5">
          <h3 class="title-gradient-border" data-title="Successful!">
            Successful!
          </h3>
          <h4 class="quiz__finish-slogan quiz-slogan">
            Tell us in which domain area your project is located.
          </h4>
          <div class="quiz__finish-buttons">
            <button
              class="btn btn-gray"
              type="button"
              @click.prevent="goToStep(0)"
            >
              <span>Go over it again</span>
            </button>
            <nuxt-link class="btn" to="/">
              <span>Go to Home Page</span>
            </nuxt-link>
          </div>
        </div>
      </form>
    </div>
    <div class="progres">
      <div class="progressbar" :style="`width: ${progres}%`"></div>
    </div>
  </section>
</template>

<script>
import { required } from 'vuelidate/lib/validators';

export default {
  data() {
    return {
      image: '',
      currentStep: 0,
      progres: 0,
      value: 0,
      backgroundSize: '0% 100%',
      step1: [
        {
          id: 1,
          visible: true,
          name: 'Blockchain ecosystem',
          list: [
            {
              id: 'step1-1-1',
              value: 'Cryptocurrencies from scratch',
              name: 'cryptocurrencies-from-scratch',
              checked: false,
            },
            {
              id: 'step1-1-2',
              value: 'Blockchain forks',
              name: 'blockchain-forks',
              checked: false,
            },
            {
              id: 'step1-1-3',
              value: 'Blockchain based platforms',
              name: 'blockchain-based-platforms',
              checked: false,
            },
            {
              id: 'step1-1-4',
              value: 'Blockchain nodes',
              name: 'blockchain-nodes',
              checked: false,
            },
            {
              id: 'step1-1-5',
              value: 'Cross-chain bridges',
              name: 'cross-chain-bridges',
              checked: false,
            },
          ],
        },
        {
          id: 2,
          visible: false,
          name: 'Decentralized application',
          list: [
            {
              id: 'step1-2-1',
              value: 'DeFi applications',
              name: 'defi-applications',
              checked: false,
            },
            {
              id: 'step1-2-2',
              value: 'Decentralized exchanges',
              name: 'decentralized-exchanges',
              checked: false,
            },
            {
              id: 'step1-2-3',
              value: 'DAO - Decentralized autonomous organization',
              name: 'dao',
              checked: false,
            },
            {
              id: 'step1-2-4',
              value: 'Staking platforms',
              name: 'staking-platforms',
              checked: false,
            },
            {
              id: 'step1-2-5',
              value: 'Crypto wallets',
              name: 'crypto-wallets',
              checked: false,
            },
            {
              id: 'step1-2-6',
              value: 'Crypto games',
              name: 'crypto-games',
              checked: false,
            },
          ],
        },
        {
          id: 3,
          visible: false,
          name: 'Smart contracts',
          list: [
            {
              id: 'step1-3-1',
              value: 'Smart contracts',
              name: 'smart-contracts',
              checked: false,
            },
            {
              id: 'step1-3-2',
              value: 'Stablecoin development',
              name: 'stablecoin-development',
              checked: false,
            },
            {
              id: 'step1-3-3',
              value: 'Security audits',
              name: 'security-audits',
              checked: false,
            },
            {
              id: 'step1-3-4',
              value: 'Token emission and distribution',
              name: 'token-emission-and-distribution',
              checked: false,
            },
          ],
        },
        {
          id: 4,
          visible: false,
          name: 'Developer tools',
          list: [
            {
              id: 'step1-4-1',
              value: 'SDKs',
              name: 'sdks',
              checked: false,
            },
            {
              id: 'step1-4-2',
              value: 'APIs',
              name: 'apis',
              checked: false,
            },
            {
              id: 'step1-4-3',
              value: 'Online/Offline IDEs',
              name: 'online-offline-ides',
              checked: false,
            },
            {
              id: 'step1-4-4',
              value: 'Plugins',
              name: 'plugins',
              checked: false,
            },
          ],
        },
        {
          id: 5,
          visible: false,
          name: 'Enterprise solution',
          list: [
            {
              id: 'step1-5-1',
              value: 'Governance (voting) systems',
              name: 'governance-systems',
              checked: false,
            },
            {
              id: 'step1-5-2',
              value: 'Logistics solutions',
              name: 'logistics-solutions',
              checked: false,
            },
            {
              id: 'step1-5-3',
              value: 'Supply chains',
              name: 'supply-chains',
              checked: false,
            },
            {
              id: 'step1-5-4',
              value: 'Compliance system',
              name: 'compliance-system',
              checked: false,
            },
          ],
        },
        {
          id: 6,
          visible: false,
          name: 'Blockchain integrations',
          list: [
            {
              id: 'step1-6-1',
              value: 'Centralized exchange',
              name: 'centralized-exchange',
              checked: false,
            },
            {
              id: 'step1-6-2',
              value: 'Decentralized marketplaces',
              name: 'decentralized-marketplaces',
              checked: false,
            },
            {
              id: 'step1-6-3',
              value: 'Blockchain based micropayment services',
              name: 'blockchain-based-micropayment-services',
              checked: false,
            },
            {
              id: 'step1-6-4',
              value: 'CRM/ERP blockchain integration',
              name: 'crm-erp-blockchain-integration',
              checked: false,
            },
          ],
        },
      ],
      step2: [
        {
          id: 1,
          visible: true,
          name: 'Blockchain',
          list: [
            {
              id: 'step2-1-1',
              value: 'Ethereum',
              name: 'ethereum',
              checked: false,
            },
            {
              id: 'step2-1-2',
              value: 'Substrate',
              name: 'substrate',
              checked: false,
            },
            {
              id: 'step2-1-3',
              value: 'Binance Chain',
              name: 'binance chain',
              checked: false,
            },
            {
              id: 'step2-1-4',
              value: 'Tezos',
              name: 'tezos',
              checked: false,
            },
            {
              id: 'step2-1-5',
              value: 'Tron',
              name: 'tron',
              checked: false,
            },
            {
              id: 'step2-1-6',
              value: 'EOS',
              name: 'eos',
              checked: false,
            },
            {
              id: 'step2-1-7',
              value: 'Corda',
              name: 'corda',
              checked: false,
            },
            {
              id: 'step2-1-8',
              value: 'Hyperledger',
              name: 'hyperledger',
              checked: false,
            },
            {
              id: 'step2-1-9',
              value: 'Solana',
              name: 'solana',
              checked: false,
            },
            {
              id: 'step2-1-10',
              value: 'Avalanche',
              name: 'avalanche',
              checked: false,
            },
            {
              id: 'step2-1-11',
              value: 'Dash / PIVX',
              name: 'dash-pivx',
              checked: false,
            },
          ],
        },
        {
          id: 2,
          visible: false,
          name: 'Back-end',
          list: [
            {
              id: 'step2-2-1',
              value: 'C++, Python',
              name: 'c-python',
              checked: false,
            },
            {
              id: 'step2-2-2',
              value: 'Rust',
              name: 'rust',
              checked: false,
            },
            {
              id: 'step2-2-3',
              value: 'Node.js, Go',
              name: 'nodejs-go',
              checked: false,
            },
            {
              id: 'step2-2-4',
              value: 'Solidity',
              name: 'solidity',
              checked: false,
            },
            {
              id: 'step2-2-5',
              value: 'TypeScript',
              name: 'typescript',
              checked: false,
            },
            {
              id: 'step2-2-6',
              value: 'JavaScript',
              name: 'javascript',
              checked: false,
            },
            {
              id: 'step2-2-7',
              value: 'SQL & NoSQL',
              name: 'sql-nosql',
              checked: false,
            },
            {
              id: 'step2-2-8',
              value: 'Redis, Elasticsearch',
              name: 'redis-elasticsearch',
              checked: false,
            },
            {
              id: 'step2-2-9',
              value: 'Docker',
              name: 'docker',
              checked: false,
            },
          ],
        },
        {
          id: 3,
          visible: false,
          name: 'Front-end',
          list: [
            {
              id: 'step2-3-1',
              value: 'Vue.js',
              name: 'vuejs',
              checked: false,
            },
            {
              id: 'step2-3-2',
              value: 'React.js',
              name: 'reactjs',
              checked: false,
            },
            {
              id: 'step2-3-3',
              value: 'Redux',
              name: 'redux',
              checked: false,
            },
            {
              id: 'step2-3-4',
              value: 'TypeScript',
              name: 'typescript',
              checked: false,
            },
            {
              id: 'step2-3-5',
              value: 'Mobx',
              name: 'mobx',
              checked: false,
            },
            {
              id: 'step2-3-6',
              value: 'RxJS',
              name: 'rxjs',
              checked: false,
            },
            {
              id: 'step2-3-7',
              value: 'GraphQL',
              name: 'graphql',
              checked: false,
            },
          ],
        },
        {
          id: 4,
          visible: false,
          name: 'Mobile',
          list: [
            {
              id: 'step2-4-1',
              value: 'Android: Java, Kotlin',
              name: 'android-java-kotlin',
              checked: false,
            },
            {
              id: 'step2-4-2',
              value: 'iOS: Objective-C, Swift',
              name: 'ios-objective-c-swift',
              checked: false,
            },
            {
              id: 'step2-4-3',
              value: 'React Native',
              name: 'react-native',
              checked: false,
            },
          ],
        },
      ],
      step3: [
        'Undetermined',
        '1-2 month',
        '3-6 month',
        '1-2 years',
        'More than 2 years',
      ],
      step4: {
        name: null,
        email: null,
        description: null,
        files: null,
      },
    };
  },

  validations: {
    step4: {
      name: {
        required,
      },
      email: {
        required,
      },
    },
  },

  methods: {
    updateValue(index) {
      this.value = index;
      const min = 0;
      const max = this.step3.length - 1;
      const val = this.value;

      this.backgroundSize = ((val - min) * 100) / (max - min) + '% 100%';
    },

    updateSlider(e) {
      const clickedElement = e.target;
      const min = clickedElement.min;
      const max = clickedElement.max;
      const val = clickedElement.value;

      this.backgroundSize = ((val - min) * 100) / (max - min) + '% 100%';
    },

    resetInputFiles() {
      this.step4.files = null;
    },

    onFileChanged(e) {
      const files = e.target.files;
      this.step4.files = files;
    },

    goToStep(step) {
      this.currentStep = step;
      this.progres = step * 20;
    },

    formSubmit() {
      this.$v.$touch();
      if (!this.$v.$invalid) {
        this.$v.$reset();
        this.step4.name = null;
        this.step4.email = null;
        this.step4.description = null;
        this.step4.files = null;
        this.value = 0;
        this.backgroundSize = '0% 100%';

        this.step1.forEach((item, index) => {
          if (index === 0) {
            item.visible = true;
          } else {
            item.visible = false;
          }
          item.list.forEach((itemList) => {
            itemList.checked = false;
          });
        });

        this.step2.forEach((item, index) => {
          if (index === 0) {
            item.visible = true;
          } else {
            item.visible = false;
          }
          item.list.forEach((itemList) => {
            itemList.checked = false;
          });
        });

        this.goToStep(5);
      }
    },
  },
};
</script>

<style scoped lang="scss" src="./index.scss" />
