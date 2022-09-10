<template>
  <section class="contact pt140">
    <div class="container">
      <div class="row">
        <div class="col-12 col-lg-5 col-xl-4">
          <div class="slogan">Talk to an expert</div>
          <h2>Contact us</h2>
          <div class="contact__info">
            <h5>Fill out the form or contact us via:</h5>
            <ul class="contact__info-list">
              <li>
                <a :href="'tel:' + phoneNumber" class="link">
                  {{ phoneNumber }}
                </a>
              </li>
              <li>
                <a :href="'mailto:' + email" class="link">
                  {{ email }}
                </a>
              </li>
              <li>{{ adr }}</li>
            </ul>
          </div>
        </div>
        <div class="col-12 col-lg-7 col-xl-8">
          <form
            action="/"
            class="contact__form"
            method="post"
            @submit.prevent="formSubmit"
          >
            <div class="contact__form-top">
              <h4>Get a quote</h4>
              <p class="contact__form-top-slogan">
                Our team will happily answer all your questions in the nearest
                possible time.
              </p>
            </div>
            <div class="contact__form-select-category">
              <div class="label">Select Type of Your Project</div>
              <ul class="tag-list">
                <li v-for="(item, index) in projectDefault" :key="index">
                  <div class="checkbox-group">
                    <input
                      v-model="form.project"
                      :value="item"
                      type="checkbox"
                    />
                    <span>{{ item }}</span>
                  </div>
                </li>
              </ul>
            </div>
            <div class="contact__form-budget">
              <div class="label">Your Budget</div>
              <ul class="tag-list">
                <li v-for="(radio, index) in budgetDefault" :key="index">
                  <div class="checkbox-group">
                    <input v-model="form.budget" type="radio" :value="radio" />
                    <span>${{ radio }} k</span>
                  </div>
                </li>
              </ul>
            </div>
            <div class="form">
              <ul class="contact__form-list-input">
                <li>
                  <div class="label">Your Full Name</div>
                  <input
                    v-model.trim="form.name"
                    type="text"
                    name="your-name"
                    :class="{
                      error: $v.form.name.$error,
                    }"
                    @input="$v.form.name.$touch()"
                  />
                  <div v-if="$v.form.name.$error" class="input-help">
                    <span v-if="!$v.form.name.required">
                      Name cannot be blank.
                    </span>
                  </div>
                </li>
                <li>
                  <div class="label">Email Adress</div>
                  <input
                    v-model.trim="form.email"
                    type="email"
                    name="your-email"
                    :class="{
                      error: $v.form.email.$error,
                    }"
                    @input="$v.form.email.$touch()"
                  />
                  <div v-if="$v.form.email.$error" class="input-help">
                    <span v-if="!$v.form.email.required">
                      E-mail cannot be blank.
                    </span>
                  </div>
                </li>
                <li>
                  <div class="label">Description (optional)</div>
                  <textarea
                    v-model.trim="form.description"
                    name="your-description"
                    placeholder="Write here what you think is important about your project"
                    maxlength="250"
                  ></textarea>
                </li>
                <li class="btn-cover">
                  <button class="btn" type="submit">
                    <span>Submit</span>
                  </button>
                </li>
              </ul>
            </div>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { required } from 'vuelidate/lib/validators';

export default {
  data() {
    return {
      phoneNumber: '+38 099 99 88 777',
      email: 'info@sitename.com',
      adr: 'Kyiv, Ukraine, 123 Metalurgov St',
      projectDefault: [
        'Blockchain Ecosystem',
        'Decentralized Application',
        'Smart Contracts',
        'Developer Tools',
        'Enterprise Solution',
        'Blockchain Integration',
        'Security Audit',
        'Technical due Diligence',
      ],
      budgetDefault: ['5-10', '11-20', '21-50', '51-100'],
      form: {
        project: [],
        budget: [],
        name: null,
        email: null,
        description: null,
      },
    };
  },
  validations: {
    form: {
      name: {
        required,
      },
      email: {
        required,
      },
    },
  },
  methods: {
    formSubmit() {
      this.$v.$touch();
      if (!this.$v.$invalid) {
        this.$v.$reset();
      }
    },
  },
};
</script>

<style scoped lang="scss" src="./index.scss" />
