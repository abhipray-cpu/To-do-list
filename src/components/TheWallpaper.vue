<template>
    <div id="container">
        <div class="row">
            <div class="item" id="item1">
         
            </div>
             <div class="item" id="item2">
                
            </div>
             <div class="item" id="item3">
               
            </div>
        </div>
        <div class="row">
             <div class="item" id="item4">
              
            </div>
             <div class="item" id="item5">
              
            </div>
             <div class="item" id="item6">
                
            </div>
        </div>
    </div>
</template>

<style scoped>
#container {
    width: 400px;
    height:200px;
    border:2px solid transparent;
    margin-left:4px;
    margin-top:10px;
    border-radius:10px;
    display: grid;
    grid-template-rows: 30fr 30fr;
   
    
}
.row{
    height:80px;
    width:100%;
    margin-top: 10px;
    margin-bottom: 10px;
    display: grid;
    grid-template-columns: 30fr 30fr 30fr;

}
.item{
    width:120px;
    height:80px;
    border:2px solid transparent;
    border-radius: 10px;
    margin-left: 5px;
    margin-right: 5px;
}


#item1{
    background-image: url('../Assets/indian.jpg');
}
#item2{
    background-image: url('../Assets/italian .jpg')
}
#item3{
    background-image: url('../Assets/chinese.jpg')
}
#item4{
    background-image: url('../Assets/pizzaa - Copy.jpg')
}
#item5{
    background-image: url('../Assets/drinks - Copy.jpg')
}
#item6{
    background-image: url('../Assets/burger - Copy.jpg')
}

</style>