<template>
  <div class="qr-code" style="display:inline-block"></div>
</template>

<script>
export default {
  name: 'Qrcode',
  props: {
    text: {
      type: String,
      default: ''
    },
    height: {
      type: Number,
      default: 200
    },
    width: {
      type: Number,
      default: 200
    }
  },
  mounted () {
    require.ensure([], (r) => {
      let QRCode = require('qrcodejs2')
      this.$qrcode = new QRCode(this.$el, {
        ...this.$props
      })
    })
  },
  watch: {
    text (value) {
      this.$qrcode.clear()
      this.$qrcode.makeCode(value)
    }
  }
}
</script>
