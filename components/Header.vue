<template>
  <header class="header" :class="{ 'header--unpinned': scrolled }">
    <div class="header__container">
      <div class="header__left">
        <nuxt-link to="/" class="logo">
          <img src="@/static/logo.svg" alt="Logo" />
        </nuxt-link>
      </div>
      <div class="header__center">
        <nav class="nav-menu" :class="{ active: menu }">
          <ul class="nav-list">
            <!-- <li v-for="(item, index) in menuList" :key="index">
              <a
                :href="'#' + item.anchor"
                @click.prevent="scrollAnchor(item)"
                >{{ item.name }}</a
              >
            </li> -->
            <li v-for="(item, index) in menuList" :key="index">
              <nuxt-link :to="{ path: '/', hash: `#${item.anchor}` }">
                <span @click.prevent="scrollAnchor(item)">{{ item.name }}</span>
              </nuxt-link>
            </li>
            <li class="mvp-menu-item">
              <nuxt-link to="/mvp">
                <span @click="hideMenu">MVP</span>
              </nuxt-link>
            </li>
          </ul>
        </nav>
      </div>
      <div class="header__right">
        <a :href="'https://wa.me/' + whatsapp" target="_blank" class="btn">
          <span>Contact me</span>
        </a>
        <button class="nav-btn" :class="{ active: menu }" @click="toggleMenu">
          <div class="nav-btn__burger"></div>
        </button>
      </div>
    </div>
  </header>
</template>
<script>
export default {
  data() {
    return {
      whatsapp: '+380999988777',
      limitPosition: 400,
      scrolled: false,
      lastPosition: 0,
      menu: false,
      menuList: [
        {
          name: 'Home',
          anchor: 'home',
        },
        {
          name: 'About Us',
          anchor: 'about',
        },
        {
          name: 'Services',
          anchor: 'services',
        },
        {
          name: 'Cases',
          anchor: 'cases',
        },
        {
          name: 'Contact',
          anchor: 'contact',
        },
      ],
    };
  },

  beforeMount() {
    window.addEventListener('scroll', this.handleScroll);
  },

  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },

  methods: {
    handleScroll() {
      if (
        this.lastPosition < window.scrollY &&
        this.limitPosition < window.scrollY
      ) {
        this.scrolled = true;
        // move up!
      }

      if (this.lastPosition > window.scrollY) {
        this.scrolled = false;
        // move down
      }

      this.lastPosition = window.scrollY;
      // this.scrolled = window.scrollY > 250;
    },

    toggleMenu() {
      this.menu = !this.menu;
      document.querySelector('body').classList.toggle('no-scroll');
    },

    hideMenu() {
      this.menu = false;
      document.querySelector('body').classList.remove('no-scroll');
    },

    scrollAnchor(item) {
      if (this.menu) {
        this.menu = false;
        document.querySelector('body').classList.remove('no-scroll');
      }
      const element = document.getElementById(item.anchor);
      if (element) {
        const y = element.getBoundingClientRect().top + window.pageYOffset - 0;
        window.scrollTo({ top: y, behavior: 'smooth' });
      } else {
        this.$router.push(`/#${item.anchor}`);
      }
    },
  },
};
</script>

<style lang="scss">
@import '~/assets/styles/variables.scss';

// HEADER SCROLL
body {
  &.no-scroll {
    overflow: hidden;
  }
}
.header--pinned {
  transform: translateY(0%);
}
.header--unpinned {
  transform: translateY(-100%);
}

.header {
  will-change: transform;
  transition: transform 0.25s linear;
  background-color: map-get($bg, 'gray');
  min-height: 80px;
  padding: 0 40px;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 10;
  display: flex;
  align-items: center;
  @media (max-width: $media_xl) {
    padding: 0 30px;
  }
  &__container {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  &__left {
    flex: 0 0 auto;
    display: flex;
    justify-content: flex-start;
  }

  &__center {
    flex-grow: 1;
    display: flex;
    justify-content: center;
  }

  &__right {
    flex: 0 0 auto;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    .btn {
      z-index: 4;
      @media (max-width: $media_lg) {
        height: 46px;
        border-radius: 12px;
      }
      @media (max-width: $media_xs) {
        height: 36px;
        font-size: 12px;
        border-radius: 8px;
        min-width: 100px;
        padding: 0;
      }
    }
  }
  .logo {
    position: relative;
    z-index: 4;
    @media (max-width: $media_xs) {
      img {
        max-width: 105px;
      }
    }
  }
}
</style>
