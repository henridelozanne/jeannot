<template>
  <div class="modal-backdrop">
    <div class="modal-content">
      <h2>{{ picto }}</h2>

      <img v-if="picto" :src="require(`~/assets/${picto}.png`)" alt="picto">

      <div class="icon-ctn">
        <a :href="require(`../assets/${picto}.png`)" :download="true">
          <DownloadIcon :data-href="`~/assets/${picto}.png`" />
        </a>

        <XmarkIcon class="cross-icon" @click.native="closeModal" />
      </div>
    </div>
  </div>
</template>

<script>
import DownloadIcon from '@/components/DownloadIcon'
import XmarkIcon from '@/components/XmarkIcon'

export default {
  name: 'PictoModal',

  components: {
    DownloadIcon,
    XmarkIcon
  },

  props: {
    picto: {
      type: String,
      default: ''
    }
  },

  methods: {
    closeModal () {
      this.$emit('close-modal')
    }
  }
}
</script>

<style lang="scss" scoped>
.modal-backdrop {
  position: fixed;
  z-index: 3;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;

  .modal-content {
    padding: 20px 80px 20px;
    background: rgb(255, 255, 255);
    z-index: 4;
    position: relative;
    border-radius: 3px;

    h2 {
      text-align: center;
      text-transform: capitalize;
      font-size: 1.9rem;
      margin-bottom: 50px;
      margin-top: 0;
    }

    img {
      max-width: 300px;
    }
    // height: 300px;

    .icon-ctn {
      position: absolute;
      top: 20px;
      right: 20px;
      display: flex;
      align-items: center;

      svg {
        width: 22px;
        cursor: pointer;

        &:hover {
          transform: scale(1.15);
          fill: rgb(46, 217, 166);
        }
      }

      .cross-icon {
        width: 18px;
        margin-left: 15px;

        &:hover {
          fill: rgb(217, 46, 46);
        }
      }
    }

  }

  @media screen and (max-width: 700px) {
    .modal-content {
      width: 90vw;
      box-sizing: border-box;

      img {
        width: 100%;
      }
    }
  }
}
</style>
