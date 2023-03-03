<template>
    <!-- <div class="spinner" v-if="spinnerDisplay">
        <Spinner/>
    </div> -->
    <div class="container">
        <div class="row justify-content-center mx-2">
            <div class="col-sm-4 my-5 proj " v-for="item in items" :key="item.id">
                <div class="card" style="width: 15rem; border: 1px solid black;">
                    <img :src="item.imgURL" class="card-img-top" alt="...">
                    <div class="card-body">
                        <router-link class="btn btn-success" :to="{name: 'singleProduct', params: {id: item.id}}">View Details</router-link>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
// import Spinner from '@/components/spinnerComponentonent.vue';
import axios from "axios";
export default {
    // components: {
    //     Spinner
    // },
    name: 'product-comp',
    data() {
        return {
            items: [],
            // spinnerDisplay: true,
        };
    },
    created() {
        this.getProducts();
    },
    methods: {
        async getProducts() {
            try {
                const response = await axios.get("https://connections4u.onrender.com/products");
                this.items = response.data.results;
                console.log(response);
            } catch (err) {
                console.log(err);
            }
        },


    },
//     mounted() {
//     setTimeout(() => {
//         this.spinnerDisplay = false
//         console.log(this.spinnerDisplay);
//     }, 2000)
// }
}
</script>

<style>
.container{
  display: inline-block;
}

.proj{
  height: 40vh;
  /* max-width: ; */
  background-size: 100%;
  border-radius:10px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.proj img{
  max-width: 100%;
  height: 12rem;
  margin-top: 10%;
}

</style>