<template>
  <div>
    {{hello}}
    {{myValue}}
    <button @click="emitMyEvent">emit</button>
    <!-- <slot>no slot</slot> -->
    <slot name="header">no header</slot>
    <p>乱七八糟</p>
    <slot name="footer">no footer</slot>
  </div>
</template>

<script>
export default {
  props: {
    'my-value': [Number, String, Object]
  },
  data () {
    return {
      hello: 'i am component a'
    }
  },
  methods: {
    emitMyEvent () {
      this.$emit('my-event', this.hello)
    }
  }
}
</script>
