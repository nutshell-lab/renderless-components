<script>
export default {
  props: {
    duration: {
      type: Number,
      default: () => 1000,
    },
  },
  data: () => ({
    show: false,
  }),
  mounted() {
    setTimeout(() => (this.show = true), this.duration)
  },
  render() {
    return this.$scopedSlots.default({
      show: this.show,
    })
  },
}
</script>
