<template>
  <div id="app">
    <TagCanvas ref="tag" :data="tags" :options="options" @click="handleClick"></TagCanvas>
  </div>
</template>

<script>
import TagCanvas from './components/tagCanvas.vue'

export default {
  name: 'App',
  components: {
    TagCanvas
  },

  data() {
    return {
      tags: [],
      options: {
        textColour: '#000',
        outlineColour: '#ff00ff',
        outlineThickness: 1,
        maxSpeed: 0.02,
        minSpeed: 0.01,
        depth: 0.75,
        initial: [1, -0.2],
        freezeActive: true,
        stretchX: 2.5,
        stretchY: 2.5,
        fadeIn: 800,
        clickToFront: 600,
        shuffleTags: true
        // textHeight: 25,

        // shadowOffset: [1, 1],
        // minBrightness: 0.2,
        // maxSpeed: 0.05,
        // minSpeed: 0.01,
        // textColour: null,
        // depth: 0.97,
        // wheelZoom: false,
        // reverse: true,
        // stretchX: 4.7,
        // initial: [0, 0.1],
        // clickToFront: 600
      }
    }
  },
  methods: {
    createTags(count) {
      let tags = []
      for (let i = 1; i < count; i++) {
        tags.push({
          text: 'Tag ' + i,
          color: '#ff0000'
        })
      }
      return tags
    },
    pause() {
      this.$refs.tag.pause()
    },
    resume() {
      this.$refs.tag.resume()
    },
    reload() {
      this.$refs.tag.reload()
    },
    update() {
      this.$refs.tag.update()
    },
    tagToFront() {
      this.$refs.tag.tagToFront({
        index: 5,
        active: 1
      })
    },
    rotateTag() {
      this.$refs.tag.rotateTag({ index: 2, lat: 30, lng: -45 })
    },
    setSpeed() {
      this.$refs.tag.setSpeed([0.5, -0.25])
    },
    handleClick(item) {
      console.log('item :', item)
    }
  },
  mounted() {
    setTimeout(() => {
      this.tags = this.createTags(100)
    }, 100)
  }
}
</script>

<style>
#app {
  width: 400px;
  height: 400px;
}
</style>
