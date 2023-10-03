<template>
    <div>
        <li class="nav-item cart">
            <a href="/home " class="nav-link"><span>Cart</span><span>{{itemCount}}</span></a>
        </li>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                itemCount: '',
            }
        },
        mounted() {
            this.$root.$on('changeInCart', (item) => {
                this.itemCount = item;
            })
        }
    }
</script>
