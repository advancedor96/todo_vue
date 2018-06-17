<template>
  <div id="app">
    <ul class="list">
      <ListItem v-for="(item, key) in orderedItems" :key="key" :item="item"/>
    </ul>
  </div>
</template>

<script>
  import ListItem from './components/ListItem.vue';


  export default {
    name: 'app',
    components: {
      ListItem
    },
    data() {
      return {
        items: [{
          title: "1錄課程",
          date: "",
          comment: "",
          star: false,
          complete: false
        }, {
          title: "2吃晚餐",
          date: "",
          comment: "",
          star: false,
          complete: false
        }, {
          title: "3喝咖啡",
          date: "",
          comment: "",
          star: false,
          complete: false
        }, {
          title: "4修理手機",
          date: "",
          comment: "",
          star: false,
          complete: false
        }]
      }
    },
    computed: {
      orderedItems(){
        return this.items.sort( (a,b)=>{
          let scoreA = (a.star? -100:0) + (a.complete? 100:0)
          let scoreB = (b.star? -100:0) + (b.complete? 100:0);
          return scoreA - scoreB;
        })
      }
    }
  }
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Roboto:300,400,500,700,900');
  $c_blue: #4A90E2;
  $c_DarkBlue: #00408B;
  $c_red: #D0021B;
  $c_yellow: #f5a623;
  $c_lightYellow: #fff2dc;
  $c_greylight: #f2f2f2;
  $c_graymid: #c8c8c8;
  $c_grayDark: #757575;



  html,
  body {
    width: 100%;
    background: #e1e1e1;
    font-family: 'Roboto', serif;
    margin: 0;
  }

  #app {
    width: 100%;
    display: flex;
    justify-content: center;
  }

  * {
    // border: 1px solid black;
    box-sizing: border-box;
  }
  ul{
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  .list{
    width: 100%;
    max-width: 620px;
  }

  
</style>