<script>
import debounce from './debounce'

export default {
  props: {
    value: {
      type: [Object, String, Number, Boolean, Array],
      default: null,
    },
  },

  data: () => ({
    debounced: null,
  }),

  watch: {
    value(v) {
      this.input(v)
    },
    debounced(v) {
      this.patchValueDebounced(v)
    },
  },

  mounted() {
    this.input(this.value)
  },

  computed: {
    patchValueDebounced() {
      return debounce(function (value) {
        this.$emit('input', value)
      }, 200)
    },
  },

  methods: {
    input(val) {
      if (val !== this.debounced) this.debounced = val
    },
  },

  render() {
    return this.$scopedSlots.default({
      debounced: this.debounced,
      debounce: this.input,
    })
  },
}
</script>
