<template>
  <section class="about pt140">
    <div class="about__wrap container">
      <div class="row">
        <div class="col-12 col-lg-5 col-xl-6">
          <div class="slogan">Who we are?</div>
          <h2>About us</h2>
        </div>
      </div>
      <div class="about__container container">
        <div class="row">
          <div class="col-12 col-lg-7 col-xl-6">
            <div class="about__list-cover">
              <ul class="about__list">
                <li v-for="(item, index) in about" :key="index">
                  <h3 class="about__list-title">{{ item.title }}</h3>
                  <p class="about__list-description secondary">
                    {{ item.description }}
                  </p>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      about: [
        {
          title:
            'We are your business partner, not just a blockchain development outsourcing firm.',
          description:
            'We focus on your business objectives and deal primarily with your business goals, not just with your TOR.',
        },
        {
          title: 'We are focused on custom blockchain development solutions,',
          description:
            'having been in this industry for a long time, and have deep expertise in every part of the blockchain ecosystem.',
        },
        {
          title: 'We can complete any complex task, whatever its size.',
          description:
            'You don’t need to outsource it to different specialists.',
        },
        {
          title: `We have experience as part of client's team and as an outsourcing subcontractor.`,
          description:
            'All our work processes are tuned so we can easily join any team.',
        },
      ],
    };
  },
};
</script>

<style scoped lang="scss" src="./index.scss" />
