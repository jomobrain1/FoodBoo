<template>
      
<div id="meals">
    <input type="text" v-model="search" class="search">
    <button @click="fetchData()">search</button>
    <div v-if="loading">
        <p class="loading">
           <h1>loading</h1>
        </p>
    </div>
    <MealCard v-else :meals="meals"></MealCard>
</div>
   
</template>

<script>
import axios from  "axios"
import MealCard from "./MealCard.vue"
    export default{
    mounted() {
        setTimeout(this.checkBox, 2000);
    },
    data() {
        return {
            search:"",
            loading:false,
            meals: []
        };
    },
    methods: {
        fetchData() {
            this.loading=true
            axios.get(`https://www.themealdb.com/api/json/v1/1/search.php?s=${this.search}`)
                .then(res => {
                    this.loading=false
                this.meals = res.data.meals;
                console.log(res.data);
                if(this.meals==null){
                  
                }
            }).catch(err => console.log(err));
            
        },
        checkBox() {
            let btn = document.querySelectorAll("#btn");
            for (let i = 0; i < btn.length; i++) {
                btn[i].onclick = (e) => {
                    e.preventDefault();
                    e.path[1].children[0].classList.toggle("block");
                    e.path[1].children[1].classList.toggle("block");
                };
            }
        }
    },
    created() {
        let items=[
            "chicken","cake","b","fry",
            "c","d","e","f","g","h","fish","pie"
        ]
        var item = items[Math.floor(Math.random()*items.length)];
        console.log(item);
        this.loading=true
        axios.get(`https://www.themealdb.com/api/json/v1/1/search.php?s=${item}`)
            .then(res => {
                this.loading=false
            this.meals = res.data.meals;
            
        })
            .catch(err => console.log(err));
    },
    components: { MealCard }
}
</script>
<style scoped>
   
input{
    width: 20rem;
    height: 2rem;
    margin: 30px 10px;
}
button{
    height: 2rem;
}
.loading{
    display: grid;
    place-content: center;
}
input:focus{
    outline: 1px solid #669;
}
</style>

