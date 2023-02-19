<template>
  <div :class="{opened: isOpened}" class="burger-menu" @click="toggleState">
    <div />
  </div>
</template>

<script>
export default {
  name: 'NavMenuMobile',

  props: {
    isOpened: {
      type: Boolean,
      default: false
    }
  },

  methods: {
    toggleState () {
      this.$emit('toggle-mobile-menu', !this.isOpened)
    }
  }
}
</script>

<style lang="scss" scoped>
.burger-menu {
  width: 30px;
}

.burger-menu:before,
.burger-menu:after,
.burger-menu div {
  background: rgb(96, 96, 96);
  content: "";
  display: block;
  height: 3px;
  border-radius: 3px;
  transition: 0.5s;
}

.burger-menu div {
  margin: 4px 0;
}
.burger-menu.opened:before {
  transform: translateY(7px) rotate(135deg);
}
.burger-menu.opened:after {
  transform: translateY(-7px) rotate(-135deg);
}
.burger-menu.opened div {
  transform: scale(0);
}

</style>
