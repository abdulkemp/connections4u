<template>
  <div class="container">
        <div class="row">
            <div class="col" v-for="item in items" :key="item.id">
                <div class="card" style="width: 18rem;">
                    <img :src="item.imgURL" class="card-img-top" alt="...">
                    <div class="card-body">
                        
                    </div>
                </div>
            </div>
        </div>
    </div>
    
</template>

<script>
import axios from "axios";
    export default {
        data() {
            return {
                items: []
            };
        },
        created(){
            this.getProducts;
        },
        methods: {
            async getProducts() {
                try{
                    const response = await axios.get("https://connections4u.onrender.com/products");
                    this.items = response.data.results;
                    console.log(response);
                } catch(err) {
                    console.log(err);
                }
            }
        }
    }
</script>

<style scoped>

</style>