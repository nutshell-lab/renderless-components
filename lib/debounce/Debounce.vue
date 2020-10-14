<script>
import debounce from './debounce'

const patchValueDebounced = debounce(function (value) {
  this.$emit('input', value)
}, 200)

export default {
  props: {
    value: {
      type: [Object, String, Number, Boolean],
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
    debounced(newValue, oldValue) {
      if (newValue !== oldValue) patchValueDebounced(newValue)
    },
  },

  mounted() {
    this.input(this.value)
  },

  methods: {
    input(val) {
      this.debounced = val
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
