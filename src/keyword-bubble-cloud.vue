<template>
  <div class="keyword-bubble-cloud" ref="container">
    <slot name="default"></slot>
  </div>
</template>

<script>
export default {
  name: "KeywordBubbleCloud",
  
  provide() {
    return {
      "keywordBubbleCloud": this
    }
  },

  data() {
    return {
      items: [],
      range: [],
      width: 0,
      height: 0,
    }
  },
  
  methods: {
    setItem(item) {
      //const randomWidth = Math.random() * 150 + 50
      //const left = Math.random() * (this.width - this.randomWidth)
      //const bottom = Math.random() * (this.height - this.randomWidth)
      item.width = item.height = randomWidth
      const r = parseInt(Math.random()*255)
      const g = parseInt(Math.random()*255)
      const b = parseInt(Math.random()*255)
      item.backgroundColor = `rgb(${r}, ${g}, ${b})`
    }
  },

  mounted() {
    this.$nextTick(() => {
      const {items} = this
      const {container} = this.$refs
      this.range = [
        Math.min(...items.map(item => item.value)),
        Math.max(...items.map(item => item.value))
      ]
      this.width = parseInt(container.offsetWidth)
      this.height = parseInt(container.offsetHeight)
      items.forEach(item => this.setItem(item))
    })
  }
}
</script>

<style>
.keyword-bubble-cloud {
  position: relative;
}
</style>
