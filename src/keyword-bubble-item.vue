<template>
  <div class="keyword-bubble-item" 
       :style="`width:${width}px;height:${height}px;line-height: ${height}px;background:${backgroundColor}`">
    {{label}}
  </div>
</template>

<script>
export default {
  name: "KeywordBubbleItem",

  props: {
    value: {
      type: Number,
      required: true
    },

    label: {
      type: [String, Number],
      default: "bubble"
    }
  },

  data() {
    return {
      width: 0,
      height: 0,
      backgroundColor: null
    }
  },

  inject: ["keywordBubbleCloud"],

  created() {
    this.keywordBubbleCloud.items.push(this)
  }
}
</script>

<style>
.keyword-bubble-item {
  border-radius: 50%;
  text-align: center;
  display: inline-block;
  vertical-align: middle;
}
</style>
