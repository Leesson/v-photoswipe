<template>
  <div id={id} class={className}>
    <div class="pswp-thumbnails">
      <a :key="index" :item="item" v-for="(item, index) in items" @click="showPhotoSwipe($event, index)" class="pswp-thumbnail">
        <slot :item="item">
          <img :src="item.src" alt="picture"/>
        </slot>
      </a>
    </div>
    <v-photoswipe
      ref="pswp"
      :isOpen="opened"
      :items="items"
      :options="options"
      @close="handleClose"
    />
  </div>
</template>

<script>
import PhotoSwipe from './photoswipe.vue'
import events from './events'
export default {
  name: 'v-photoswipe-gallery',
  components: {
    'v-photoswipe': PhotoSwipe
  },
  props: {
    items: {
      type: Array,
      required: true
    },
    options: {
      type: Object,
      default: {}
    },
    isOpen: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      opened: this.isOpen,
      opts: {}
    }
  },
  watch: {
    isOpen (val, oldVal) {
      if (val !== this.opened) {
        this.opened = val
      }
    }
  },
  methods: {
    showPhotoSwipe (e, index) {
      e.preventDefault()
      this.opts = Object.assign(this.options, {
        index
      })
      this.opened = true
    },
    handleClose () {
      this.opened = false
    }
  },
  mounted () {
    events.forEach(e => {
      this.$refs.pswp.$on(e, (...args) => {
        args.unshift(this)
        this.$emit(e, [...args])
      })
    })
  }
}
</script>

<style lang="css">
  .pswp-thumbnails .pswp-thumbnail {
    font-size: 0;
    cursor: pointer;
  }
</style>
