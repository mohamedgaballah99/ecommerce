<template>
<div class="products">
    <div class=" mainpro">
        <div class="container" >
            <h5><span>Select</span> A Category</h5>
            <select class="form-select" v-model="select">
                <option value="Accessories" selected>Accessories</option>
                <option value="Health&GYM">Health&GYM</option>
                <option value="Jewellery">Jewellery</option>
                <option value="Food">Food</option>
                <option value="Shoes">Shoes</option>
                <option value="Fashion">Fashion</option>
                <option value="TV">TV</option>
                <option value="Home">Home</option>
                <option value="Smartphone">Smartphone</option>
                <option value="Camera">Camera</option>
                <option value="Motors">Motors</option>
                <option value="Electronics">Electronics</option>
                <option value="Laptop">Laptop</option>
                <option value="Bags">Bags</option>
            </select>
            
            <div class="row">
                <div class=" col-lg-3 parent" v-for="pro in result" :key="pro.id" v-show="pro.category == this.select">
                        <div class="card img">
                        <img :src="pro.image" alt="pro">
                    </div>
                    <div class="card-body info">
                        <h6 class="card-title"><span>Name: </span>"{{pro.name.split(" ",1)[0]}}"</h6>
                        <h6><span>Price:</span> {{pro.price}} <span>$</span> </h6>
                        <h6><span>Quantity:</span> {{pro.quantity}}</h6>
                        <h6><span>Category:</span> "{{pro.category}}"</h6>
                        <h6><span>Subcategory:</span>"{{pro.subcategory[0].split(" ",1)[0]}}"</h6>
                        <!-- // <a href="#" class="btn btn-orange">Add To Cart</a> -->
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
// @ is an alias to /src
import axios from "axios"

export default {
    name: "Home",
    components: {

    },
    data() {
        return {
            result: null,
            select:"Accessories",
            dis:"block"
        }

    },
    mounted() {
        axios
            .get('https://e-commerce-backend-2022.herokuapp.com/product')
            .then(response => (this.result = response.data)) 
    },
   
    

};

</script>

<style lang="scss" scoped>
@import "../../sass/main.scss";

.mainpro {
    
    .container {
        h5{
            margin-top: 30px;
            font-size: 17px;
            span {
                        color: $seccolor;
                        font-weight: bold;
                    }
        }
        .form-select{
            width: 500px ;
            margin: 20px auto 30px 0px;
        }
        .row {
            >div {
                margin-bottom: 30px;
                transition: 0.3s ease-in-out;
                box-shadow: 0px 0px 10px transparent;
                padding-top: 10px;

                &:hover {
                    box-shadow: 0px 0px 10px $pricolor;
                    border-radius: 20px;

                }
            }

            .img {
                width: 13rem !important;
                margin: auto;

                img {
                    width: 100% !important;
                    height: 150px !important;
                }
            }

            .info {
                text-align: left;
                width: 100% !important;
                line-height: 2;

                h6,
                p {
                    color: $seccolor;
                    font-size: 14px;

                    span {
                        color: $pricolor;
                        font-weight: bold;
                    }
                }

                p {
                    color: gray;
                }
            }

        }
    }
}

/* Extra small devices (phones, 600px and down) */
@media only screen and (max-width: 900px) {
    .products {
        .mainpro {
            .container {
                .form-select{
            width: 250px ;
            margin: 20px auto 30px 0px;
        }
                .row {
                    .parent {
                        padding: 0px !important;
                        width: 47% !important;
                        margin: 20px auto;

                        .img {
                            width: 8rem !important;

                            img {
                                width: 90% !important;
                                height: 150px !important;
                                margin-right: auto !important;
                            }
                        }

                        .info {

                            h6,
                            p {
                                color: $seccolor;
                                font-size: 12px;

                                span {
                                    color: $pricolor;
                                    font-weight: bold;
                                    font-size: 11px;
                                }
                            }

                            p {
                                color: gray;
                            }

                            .btn {
                                font-size: 11px !important;
                                padding: 5px !important;
                            }
                        }
                    }
                }
            }
        }
    }
}
</style>
