<template lang='pug'>
  button.button(@click='onClick', :class='[...colorClass, ...sizeClass]')
    .icon(v-if='icon', :class='[...sizeClass]')
      i(:class='iconClass')
    span(v-if='hasContent')
      slot
</template>

<script>
import colorMixin from '../../../mixins/color'
import iconMixin from '../../../mixins/icon'
import routeMixin from '../../../mixins/route'
import sizeMixin from '../../../mixins/size'

export default {
  name: 'vulma-button',
  mixins: [colorMixin, iconMixin, routeMixin, sizeMixin],
  data() {
    return {
      hasContent: false
    }
  },
  mounted() {
    this.hasContent = Boolean(this.$slots.default)
  },
  methods: {
    onClick: function () {
      this.$emit('click')
      this.redirect()
    }
  }
}
</script>
