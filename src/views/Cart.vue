<template>
<div class="cart">
    <div class="container">
        <h3 class="shop"><span>Shopping</span> Cart</h3>
        <div class="img">
            <img src="@/assets/empty.gif" alt="emptyCart">
            <h3><span>Empty</span> Cart<span>..!</span></h3>
            <router-link to="/products" class="browse btn-orange">Browse Products</router-link>
        </div>

    </div>
</div>
</template>

<script>
export default {
    name: "Cart",
}
</script>

<style lang="scss" scoped>
@import "@/sass/main.scss";

.cart {
    .container {
        .shop {
            text-align: left;
        }

        h3 {
            color: $pricolor;
            font-family: cursive;
            font-weight: bold;
            margin-top: 120px;
            text-align: center;

            span {
                color: $seccolor;
            }

        }

        .img {
            width: 200px;
            margin: 0px auto;

            img {
                width: 100%
            }

            .browse {
                color: white;
                text-decoration: none;
                text-align: center;
                display: block;
                border-radius: 20px;
                padding: 10px 0px;
                font-family: cursive;
                margin-top: 10px
            }
        }

    }
}

/* Extra small devices (phones, 600px and down) */
@media only screen and (max-width: 900px) {
    .img {
        margin-top: 70px !important;
    }
}
</style>
