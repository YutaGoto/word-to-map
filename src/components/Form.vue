<template>
  <div>
    <label class="label">単語</label>
    <div class="field">
      <div class="control">
        <input class="input" type="text" placeholder="けっこう">
      </div>
    </div>
    <div class="field">
      <div class="control">
        <input class="input" type="text" placeholder="さむい">
      </div>
    </div>
    <div class="field">
      <div class="control">
        <input class="input" type="text" placeholder="やきざかな">
      </div>
    </div>

    <div class="field">
      <div class="control">
        <button class="button is-link" v-on:click="setWords()">検索</button>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
  export default {
    name: 'Form',
    methods: {
      setWords: function () {
        const elements = document.getElementsByClassName('input')
        const words = []
        for (var i = 0; i < elements.length; i++) {
          words.push(elements[i].value)
        }
        this.$emit('post', words)
      }
    }
  }
</script>
