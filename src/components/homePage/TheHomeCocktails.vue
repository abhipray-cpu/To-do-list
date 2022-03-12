<template>
  <div id="Baap">
    <div id="body">
      <!--this search will also route to receipe component with search ID-->
      <the-search @EmitValue="ProcessValue"></the-search>
      <the-wallpaper></the-wallpaper>
      <div id="minContain">
        <the-menu @switch="ChangeComponent"></the-menu>
        <the-grid2></the-grid2>
      </div>
    </div>
  </div>
</template>



<script>
//fetch data from the api and make it working
import TheSearch from '../TheSearch.vue';
import TheWallpaper from '../TheWallpaper.vue';
import TheMenu from '../TheMenu.vue';
import TheGrid2 from '../TheGrid2.vue';

export default {
  components: {
    TheSearch,
    TheWallpaper,
    TheMenu,
    TheGrid2,
  },
  inject: ['searchReq', 'changeComponent'],

  methods: {
    ProcessValue(value) {
      this.searchReq(value);
    },
    ChangeComponent() {
      this.changeComponent();
    },
  },
  data(){
   return{
     cocktail1: [{
       name:"Jal Jeera Mojito", image: "https://i.pinimg.com/564x/09/6e/49/096e49f647f893776038d525111dad0d.jpg"
     },
     {
       name:"Tamarind Ginger Magrita", image: "https://i.pinimg.com/564x/73/7f/25/737f259385ad5d4c9145e34cc93bee2f.jpg"
     },
     {
       name:"Boozy Mango Lassi", image: "https://i.pinimg.com/564x/91/76/8b/91768bc3ffa4e0b5bc9c1d404b5bb915.jpg"
     }],
      cocktail2: [{
       name:"Jade Cocktail", image:"https://mixthatdrink.com/wp-content/uploads/2010/09/jade-cocktail-600x600.jpg"
     },
     {
       name:"Lychee Martini", image: "https://mixthatdrink.com/wp-content/uploads/2011/03/lychee-liqueur-martini--800x800.jpg"
     },
     {
       name:"Blood Orange Margarita", image:"https://mixthatdrink.com/wp-content/uploads/2014/05/blood-orange-margarita-2-768x1152.jpg" 
     }],
      cocktail3: [{
       name:"Yogurt Soju", image: "https://res.klook.com/image/upload/fl_lossy.progressive,q_85/c_fill,w_680/fl_lossy.progressive,q_85/c_fill,w_680/fl_lossy.progressive/q_auto/f_auto/c_fill/blogen/image3-17.webp"
     },
     {
       name:" Cojinganmek (Cola + Soju + Beer)", image: "https://res.klook.com/image/upload/fl_lossy.progressive,q_85/c_fill,w_680/fl_lossy.progressive,q_85/c_fill,w_680/fl_lossy.progressive/q_auto/f_auto/c_fill/blogen/image8-16.webp"
     },
     {
       name:" Ujjujju Melony (Melona + Soju + Chilsung Cider)", image: "https://res.klook.com/image/upload/fl_lossy.progressive,q_85/c_fill,w_680/fl_lossy.progressive,q_85/c_fill,w_680/fl_lossy.progressive/q_auto/f_auto/c_fill/blogen/image7-18.webp"
     }],
      cocktail4: [{
       name:" Spritz Veneziano (Aperol Spritz)", image: "https://cf.ltkcdn.net/cocktails/images/std/260232-800x496r1-Aperol_Spritz.webp"
     },
     {
       name:"Bellini", image: "https://cf.ltkcdn.net/cocktails/images/std/260233-800x501r1-Bellini_cocktail.webp"
     },
     {
       name:"Negroni", image: "https://cf.ltkcdn.net/cocktails/images/std/260237-800x479r1-negroni_cocktail.webp"
     }],
      cocktail5: [{
       name:"Sidecar", image: "https://cf.ltkcdn.net/cocktails/images/std/260206-800x599r1-Sidecar_cocktail.webp"
     },
     {
       name:"1789", image:"https://cf.ltkcdn.net/cocktails/images/std/260164-800x564r1-1789-cocktail.webp"
     },
     {
       name:"Rose Cocktail", image: "https://cf.ltkcdn.net/cocktails/images/std/260168-800x533r1-Rose_cocktails.webp"
     }],
      cocktail6: [{
       name:"Austin", image: "https://cdn.vox-cdn.com/thumbor/jsm95FbknsAfZJ4rt6NsTVDbWY4=/0x0:699x626/1120x0/filters:focal(0x0:699x626):format(webp):no_upscale()/cdn.vox-cdn.com/uploads/chorus_asset/file/3645636/Screen_Shot_2015-04-27_at_9.53.42_AM.0.png"
     },
     {
       name:"ThePeachedTortilla", image: "https://cdn.vox-cdn.com/thumbor/cA5APlIMTLfjLQ-SZ3EBJ38G76E=/0x0:781x668/1120x0/filters:focal(0x0:781x668):format(webp):no_upscale()/cdn.vox-cdn.com/uploads/chorus_asset/file/3645644/unnamed.0.jpg"
     },
     {
       name:"Boston", image: "https://cdn.vox-cdn.com/thumbor/-BnYrgCCA_ijokubeQHlWznS-LM=/0x0:890x668/1120x0/filters:focal(0x0:890x668):format(webp):no_upscale()/cdn.vox-cdn.com/uploads/chorus_asset/file/3648164/unnamed.0.jpg"
     }],
      cocktail7: [{
       name:"CocaCola", image: "data:image/jpeg;base64,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"
     },
     {
       name:"Sprite", image: "data:image/jpeg;base64,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xXq1rutD1FPuLkgiIhuEREAREQBERAEREAREQBERAERECPkapdaZ5GXaKkKPgFoV7C2eRjhZzXvaQeBDiCPaFu0Y0XIo9oXyomqVScSjKUKTiXP9RQ1tTJPqtN625mnktV6w1marUxgar9C8r01GbmRq9P0XlfjhcLCNLEdUaqL2mcipWpGah9pHJdUWWz2ckfQHRX81UnhJ+LIraqp0Xwluy6QOFiWvcPRdI97T6wQfWrWuq0PTUlaEeS+gREWToEREAREQBERAEREAREQBERAEREBQt9ejGnrnmoY8wTnVzQHMeeBezLPvBHfdcq2pudV0cnVSGN2V2uBOF7dLjL3FfSSht49gR1bA19w5lyx41F7XHgbD2LDSZyqUYT7yOIUey6k6RB3hIz8yFvChqm/7LJ6nRn4OV4/+IVMf7NzXjv8A/f5LLHQ1jdYGu8Cf8K17NEGfwnZ5a39Tn80tR9KnlH3QfgtGWST/AHTx90rqEkExyNKff+ih67Ykz9KYj2/osdmjX/EUL3u/UobesP8AZu9i2GUsx0iefUP1VpZuvODfyc+136KaodmzNtekv+9/hTs0Z/xNHi/b8HP/ACSp4QP9rR8SsckVUNYreL2fkV1kRTWypBfvv+i1Z9hVMv8AZxs9QP5hZ7NGV8J2Zaps5INm1MjwwYcTiGgAkkkmwGnNdD3c6I4mlstdJ1zhY9U27YweTjq/wyHirHsPc8RStnkdic3MDgDa17Ad/G6tyyopEunstKn3UY2MAAAAAAsAMgBwACyIi2JAREQBERAEREAREQBERAEREAREQBERAEREAREQBERAEREAREQBERAEREAREQBERAEREAREQBERAEREAREQBERAEREAREQBERAEREAREQBERAEREAREQBERAEREAREQH//Z"
     },
     {
       name:"Fanta", image: "https://m.media-amazon.com/images/I/71UohdlNPYL._SL1500_.jpg"
     }],
      cocktail8: [{
       name:"Ginza Spritz", image: "https://www.kobejones.com.au/wp-content/uploads/2018/03/Kobe-Jones-Japanese-Inspired-Cocktails-2.jpg"
     },
     {
       name:"Tangerine Ginger Sake Sangria", image:"https://www.kobejones.com.au/wp-content/uploads/2018/03/Kobe-Jones-Japanese-Inspired-Cocktails-3.jpg" 
     },
     {
       name:"Shochu Melon Citrus Cocktail", image: "https://www.kobejones.com.au/wp-content/uploads/2018/03/Kobe-Jones-Japanese-Inspired-Cocktails-4.jpg"
     }],
      cocktail9: [{
       name:"Palomo Cocktail", image: "https://www.acouplecooks.com/wp-content/uploads/2020/01/Paloma-007.jpg"
     },
     {
       name:"Michelada", image: "https://www.acouplecooks.com/wp-content/uploads/2020/05/Michelada-008.jpg"
     },
     {
       name:"Cantarito", image: "https://www.acouplecooks.com/wp-content/uploads/2021/10/Cantarito-052.jpg"
     }],
   }
  },

  provide() {
    return {
     
 Row1Cocktail: {
        title: 'Indian',
        items: this.cocktail1
      }, Row2Cocktail: {
        title: 'Chinese',
        items: this.cocktail2
      }, Row3Cocktail: {
        title: 'Korean',
        items:this.cocktail3
      },
      Row4Cocktail: {
        title: 'Italian',
        items: this.cocktail4
      },
       Row5Cocktail: {
        title: 'French',
        items: this.cocktail5
      },
       Row6Cocktail: {
        title: 'Thai',
        items: this.cocktail6
      },
       Row7Cocktail: {
        title: 'Soft Drinks',
        items: this.cocktail7
      }
      ,
       Row8Cocktail: {
        title: 'Japanese',
        items: this.cocktail8
      },
       Row9Cocktail: {
        title: 'Mexican',
        items: this.cocktail9
      }
    };
  },
};
</script>


<style scoped>
#Baap {
  background-color: rgb(2, 2, 63);
}
#body {
  margin-left: 35%;
  border: 2px solid black;
  border-radius: 10px;
  width: 414px;
  height: 800px;
  padding: 2px;
  overflow-y: auto;
  background-color: white;
}
#body::-webkit-scrollbar {
  display: none;
}

#minContain {
  display: grid;
  grid-template-columns: 20fr 80fr;
  overflow-x: auto;
}
#minContain::-webkit-scrollbar {
  display: none;
}
</style>