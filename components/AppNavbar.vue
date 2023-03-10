<template>
  <nav :class="{'mobile-menu-opened': mobileMenuIsOpened}">
    <div class="logo-and-text" @click="goToHome">
      <div class="logo-ctn">
        <div class="circle" />
        <div class="circle" />

        <span>A</span>
        <span class="espelet">&</span>
        <span>A</span>
      </div>

      <h1 class="website-title">
        Autism & Advice
      </h1>
    </div>

    <NavMenuMobile class="mobile-menu" :is-opened="mobileMenuIsOpened" @toggle-mobile-menu="toggleMobileMenu" />
    <ul class="desktop-menu">
      <li>
        <router-link to="/">
          Présentation
        </router-link>
      </li>

      <li>
        <router-link to="/auticto">
          Auticto
        </router-link>
      </li>

      <li>
        <a target="_blank" href="mailto:autismnadvice@gmail.com”">Contact</a>
      </li>
    </ul>
  </nav>
</template>

<script>

export default {
  name: 'AppNavbar',

  props: {
    mobileMenuIsOpened: {
      type: Boolean,
      default: false
    }
  },

  methods: {
    goToHome () {
      this.$router.push('/')
    },

    toggleMobileMenu (value) {
      this.$emit('toggle-mobile-menu', value)
    }
  }
}
</script>

<style lang="scss">
nav {
  padding: 20px 30px 20px 40px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.15);
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 97px;
  box-sizing: border-box;

  .desktop-menu {
    display: none;
    list-style-type: none;
  }

  @media screen and (min-width: 768px) {
    .desktop-menu {
      display: flex;

      a {
        text-decoration: none;
        color: #646668;
      }

      li:not(:first-of-type) {
        margin-left: 30px;
      }

      li:hover {
        opacity: 0.7;
      }
    }

    .mobile-menu {
      display: none;
    }
  }

  &.mobile-menu-opened {
    box-shadow: none;

    .logo-and-text {
      opacity: 0;
    }
  }

  &:not(.mobile-menu-opened) {
    background: white;
  }

  .logo-and-text {
    width: fit-content;
    cursor: pointer;

    &:hover {
      opacity: 0.65;
    }

    .logo-ctn {
      position: relative;
      width: fit-content;
      margin: 0 auto;
      width: 80px;
      height: 40px;

      .circle {
        width: 40px;
        height: 40px;
        border-radius: 50%;
        border: 1px solid black;
        position: absolute;
        box-sizing: border-box;

        &:first-of-type {
          left: 8px;
        }

        &:last-of-type {
          right: 8px;
        }
      }

      span {
        position: absolute;
        top: 49%;
        transform: translateY(-50%);

        &:first-of-type {
          left: 17px;
        }

        &:last-of-type {
          right: 17px;
        }

        &.espelet {
          font-size: 0.7rem;
          left: 50%;
          transform: translate(-50%, -50%);
        }
      }
    }

    .website-title {
      cursor: pointer;
      text-transform: uppercase;
      margin: 0;
      font-size: 0.6rem;
      text-underline-offset: 3px;
      transition: all 1s ease;
      font-weight: 700;
      letter-spacing: 4px;
      margin-top: 5px;
      text-align: center;
    }
  }

}
</style>
