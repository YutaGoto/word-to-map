<template>
  <div class="index">
    <Form @post="postWords" />
    <Map :lat="lat" :lng="lng" :mapUrl="mapUrl" />
    <div class="container">
      <a class="button is-black" href="https://github.com/YutaGoto/word-to-map" target="_blank">GitHub</a>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'
  import Form from './Form.vue'
  import Map from './Map.vue'

  export default {
    name: 'Index',
    components: {
      Form,
      Map
    },
    data () {
      return {
        mapUrl: 'https://w3w.co/camp.pinch.bikers',
        lng: 35.6812409,
        lat: 139.7670057,
      }
    },
    methods: {
      postWords: function (words) {
        const word_str = words.join('.')
        const encoded_word = encodeURI(word_str)
        const url = `https://api.what3words.com/v3/convert-to-coordinates?key=${process.env.VUE_APP_WHAT_3_WORDS_KEY}&words=${encoded_word}&format=json&z=8`
        axios.get(url)
          .then(res => {
            this.lng = res.data.coordinates.lng
            this.lat = res.data.coordinates.lat
            this.mapUrl = res.data.map
          })
          .catch(err => {
            console.log(err)
            alert(err)
          })
      }
    }
  }
</script>

<style scoped>

</style>
