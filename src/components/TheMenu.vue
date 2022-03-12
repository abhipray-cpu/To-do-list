<template>
    <div>
        <div><button @click="$emit('switch','form')"><h1>+</h1></button></div>
        <div><button @click="changeDisplay"><img src="../Assets/bars-solid.svg" alt=""></button></div>
        
    <div id="menu" :style="{display:display}">
        <h1>Cuisines</h1>
         <div class="section">
             <div class="item" @click="this.redirect('Indian')">
                 <h4>Indian</h4>
                <div class="min-divider"></div>
             </div>
             <div class='item' @click="this.redirect('Chinese')">
                 <h4>Chinese</h4>
             <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirect('Korean')">
                 <h4>Korean</h4>
             <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirect('Italian')">
                  <h4>Italian</h4>
             <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirect('French')">
                 <h4>French</h4>
             <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirect('Thai')">
                 <h4>Thai</h4>
             <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirect('FastFood')">
                 <h4>Fastfood</h4>
             <div class="min-divider"></div>
             </div>
            <div class="item" @click="this.redirect('Japanese')">
                 <h4>Japanese</h4>
             <div class="min-divider"></div>
            </div>
           
            <div class="item" @click="this.redirect('Mexican')">
                 <h4>Mexican</h4>
            
            </div>
             

         </div>
         <div class="divide"></div>
         <div class="section">
             <h1 style="margin-top:2px">Drinks</h1>
             <div class="item" @click="this.redirect('Cocktails')">
                   <h4>Cocktails</h4>
                   <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirect('Coffee')">
                   <h4>Coffee</h4>
                   <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirect('Tea')">
                   <h4>Tea</h4>
                   <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirect('Shakes')">
                   <h4>Shakes</h4>
                   <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirect('Smoothies')">
                   <h4>Smoothies</h4>
             </div>
         </div>
         <div class="divide"></div>
         <div class="section">
             <h1 style="margin-top:2px">Products</h1>
             <div class="item" @click="this.redirectIngredient('Seafood')">
                   <h4>Seafood</h4>
                   <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirectIngredient('White meat')">
                   <h4>White meat</h4>
                   <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirectIngredient('Dark meat')">
                   <h4>Dark meat</h4>
                   <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirectIngredient('Vegetables')">
                   <h4>Vegetables</h4>
                   <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirectIngredient('Fruits')">
                   <h4>Fruits</h4>
                   <div class="min-divider"></div>
             </div>
             <div class="item" @click="this.redirectIngredient('Dairy')">
                   <h4>Dairy Products</h4>
             </div>
         </div>
    </div>
    </div>
</template>


<script>
export default {
    inject:['redirect','redirectIngredient'],
    data(){
        return{
            display: 'none',
        }
    },
    methods:{
        changeDisplay(){
            if(this.display == 'none'){
                this.display = 'block';
                console.log(this.display);
            }
            else if(this.display == 'block')
            {
                this.display = 'none';
                console.log(this.display);
            }
        }
    }
}
</script>

<style scoped>
#menu{
    width:150px;
    height:fit-content;
    margin-right:10px;
    margin-top:10px;
    background-color:rgb(80, 79, 79);
    margin-left:0px;
}
#menu h1{
    text-align: center;
    color: white;
    font-weight: bolder;
    margin-bottom:10px
    }
.divide{
width:100%;
height:3px;
background-color:gray;
margin-top:3px;
margin-bottom:3px;
}
.section h4{
    margin-left: 10px;
    color:white;
    font-size: 18px;
    margin-top: 0px;
    }
.min-divider{
    width:100%;
    height:1px;
    background-color:gray;
    margin-bottom: 2px;


}

.item h4{
    margin-bottom: 2px;
}

.item{
    margin-top: 1px;
    margin-bottom: 1px;
}
.item:hover{
    background-color:rgb(153, 151, 151)
}

div button img{
    height:30px;
    width:30px
}
div button{
    background-color:transparent;
    border: none;
}

</style>