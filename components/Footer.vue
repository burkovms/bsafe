<template>
  <footer class="footer">
    <div class="footer__container">
      <div class="footer__col">
        <div class="copyright">
          Copyright © <nuxt-link to="/">bSAFE</nuxt-link> - blockchain
          development company 2021
        </div>
      </div>
      <div class="footer__col">
        <ul class="social">
          <li>
            <nuxt-link to="#" target="_blank">
              <img src="~/assets/img/social/soc-tweeter.svg" alt="" />
            </nuxt-link>
          </li>
          <li>
            <nuxt-link to="#" target="_blank">
              <img src="~/assets/img/social/youtube.svg" alt="" />
            </nuxt-link>
          </li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<script>
export default {};
</script>

<style lang="scss">
@import '~/assets/styles/variables.scss';

.footer {
  background-color: map-get($bg, 'dark-400');
  display: flex;
  align-items: center;
  padding: 10px 40px;
  min-height: 72px;
  @media (max-width: $media_xl) {
    padding: 10px 30px;
  }
  &__container {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
}
.copyright {
  font-size: $font_size - 2px;
  line-height: 1.2;
  color: map-get($colors, 'gray');
  @media (max-width: $media_xs) {
    font-size: $font_size - 4px;
  }
  a {
    color: map-get($colors, 'gray');
    &:hover {
      color: map-get($colors, 'purple');
    }
  }
}
</style>
