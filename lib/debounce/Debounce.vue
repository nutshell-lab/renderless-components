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
    debounced: patchValueDebounced,
  },

  mounted() {
    this.debounced = this.value
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
