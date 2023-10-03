<template>
    <div>
      <span class="product-action">
        <a href="#!" v-on:click.prevent="addProductToCart()">Add to cart</a>
      </span>
    </div>
</template>

<script>
    export default {
        data(){

        },
        props:['productId', 'userId'],
        methods:{
            async addProductToCart(){
                if(this.userId == 0){
                    alert('You are not logged in');
                    return;
                }

                let response = await axios.post('/cart', {
                    'product_id': this.productId
                });

                this.$root.$emit('changeInCart', response.data.items);
            }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
