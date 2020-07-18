<template>
  <div>
    <p>{{ lat }}</p>
    <p>{{ lng }}</p>
    <a v-bind:href="mapUrl" target="_blank"> 詳細地図 </a>
    <figure class="image is-16by9">
      <iframe class="has-ratio" width="640" height="360" v-bind:src="embedUrl"></iframe>
    </figure>
  </div>
</template>

<script type="text/javascript">
  export default {
    name: 'Map',
    props: {
      lat: Number,
      lng: Number,
      mapUrl: String,
    },
    data () {
      return {
        embedUrl: ""
      }
    },
    updated: function () {
      this.embedUrl = `https://maps.google.co.jp/maps?output=embed&q=${this.lat},${this.lng}`
    }
  }
</script>

<style scoped="">
</style>
