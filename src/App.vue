<template>
  <div id="app">
    <yandex-map 
    :coords="coords"
    :zoom="17" 
    @click="onClick"
  >
    <ymap-marker 
      :coords="coords" 
      marker-id="123" 
      hint-content="some hint" 
    />
  </yandex-map>
  <!-- <div v-bind:class="inputStyle" class="onMap">
      <label for="title">
        <input v-on:input="inputChangeHandler" class="add-input" type="text" name="title" id="title" placeholder="Название"/>
      </label>
      <button @click="btnClick" class="button" >Добавить</button>
  </div> -->
  <div class="list-section">
    <ul class="list">
      <li @click="clickList" class="list-item" v-bind:id="item.id" v-for="item in list">{{ item.title }}</li>
    </ul>
  </div>
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
      list:[
        {id: 1, title: 'Мегафон', coords: [38.57109632819477, 68.76540318606226]},
        {id: 2, title: 'Asian-Exxpress', coords: [38.571294262263606, 68.75634268400998]},
        {id: 3, title: 'Филармония', coords: [38.56335855557847, 68.75355283017647]},
        {id: 4, title: 'Шарки Озод', coords: [38.55891433187001, 68.76914303083362]},
        {id: 5, title: 'Хотам П.В', coords: [38.58788504739466, 68.7315342361252]},
        {id: 6, title: 'Цирк', coords: [38.55769025942112, 68.76381709689171]},
        {id: 7, title: 'Зоопарк', coords: [38.58495731726059, 68.77211205415828]},
      ],
      settings: {
        apiKey: 'c1db8634-cc99-42a4-9ad9-e326c3e84e32',
        lang: 'ru_RU',
        coordorder: 'latlong',
        enterprise: false,
        version: '2.1'
      },
      // inputStyle: 'none',
      // inputValue: '',
      coords: [38.57109632819477, 68.76540318606226],
    }
  }, 
  methods: {
        onClick(e) {
        this.coords = e.get('coords');
        console.log(this.coords);
        // this.inputStyle = 'block';
        },
        clickList(e){
          this.coords = this.list[e.target.id - 1].coords;
        }

        // inputChangeHandler(e){
        //   this.inputValue = e.target.value;
        // },
        // btnClick(e){
        //   this.inputStyle = 'none';
        //   this.myPoints.push(this.inputValue)
        //   this.inputValue = '';
        // }
      },
}
</script>

<style scoped>
#app {
  width: 1000px;
  height: 500px;
  position: relative;
}

.ymap-container {
  height: 100%;
}
ul li{
  max-width: 200px;
  list-style: none;
  margin-top: 2px;
  padding-top: 10px;
  border-bottom: 1px solid #333;
  text-align: center;
  cursor: pointer;
}
ul li:hover{
  background-color: #ccc;
  transition: 0.7s;
}
/* .onMap{
  position: absolute;
  top: 0;
}
.add-input{
  padding: 10px 20px;
  outline: none;
}
.button{
  padding: 10px 5px;
}
.none{
  display: none;
}
.block{
  display: block;
} */
</style>
