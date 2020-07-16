<template>
  <div>
    <slot :list="items" :length="length" :selectItem="select" :unselectItem="unselect" />
  </div>
</template>

<script>
export default {
  props: {
    idField: {
      type: String,
      default: () => 'id'
    }
  },
  data: () => ({
    items: []
  }),
  computed: {
    length() {
      return this.items.length
    }
  },
  methods: {
    sameId(x) {
      return i =>i[this.idField] === x[this.idField]},
    select(x) {
      if(!this.items.find(this.sameId(x))) this.items.push(x)
    },
    unselect(x) {
      this.items = this.items.filter(i => !this.sameId(x)(i))
    }
  }
}
</script>
