<template>
  <div id="app">
    <yandex-map :settings="settings" :coords="coords" zoom=10>
      <ymap-marker 
        :coords="coords"
        marker-id="123123"
        marker-type="placemark"
      />
    </yandex-map>
  </div>
</template>

<script>

import { yandexMap, ymapMarker } from 'vue-yandex-maps'

export default {
  name: 'App',
  components: {
    yandexMap,
    ymapMarker
  },
  data() {
    return {
      settings: {
        apiKey: 'c1db8634-cc99-42a4-9ad9-e326c3e84e32',
        lang: 'ru_RU',
        coordorder: 'latlong',
        enterprise: false,
        version: '2.1'
      },
      coords: [54.82896654088406, 39.831893822753904]
    }
  }
}
</script>

<style scoped>
#app {
  width: 1000px;
  height: 1000px;
}

.ymap-container {
  height: 100%;
}
</style>
