<template>

<section class="meals">
<div v-for="(meal,index) in meals" :key="index" >          

     <h1>{{meal.strMeal}}</h1>        
    <div class="meal_image">
            <img :src="meal.strMealThumb" :alt="meal.strMealThumb">
    </div>
          
    <div class="meal_paragraph">
            <p class="sub" > {{meal.strInstructions.substring(0,50)}}</p>
            <p class="block"> {{meal.strInstructions}} </p>
                    
    </div>   
</div>

</section>
        
        
    </template>
    
    
    <script>
    export default{
    props:['meals']
    }
    </script>
    
    <style scoped>
  *{
        font-family: 'Roboto Mono', monospace;
    }
.meals{
    display: flex;
    flex-wrap: wrap;
    gap: 1em;
    justify-content: center;
    background: #ecf0f3;
    padding: 50px 10px;
    border-radius: 10px;
}
.meal_paragraph{
    padding: 10px 30px;
}
.meals >*{
  flex-basis: 30%;
  min-width: 10rem;
  border: 1px solid #000;
  border-radius: 20px;
  box-shadow: -3px -3px 7px #fff, 3px 3px 5px #ceced1;
}
img{
    max-width: 100%;
    border-radius: 20px;
}
.meal_image{
    padding: 3px 50px;
}
.block{
    display: none;
}
    </style>
