<template>
    <div class='v-catalog-item'>
        <img class="v-catalog-item__image" v-bind:src="require('../assets/images/' + product_data.image)" alt="img">
        <p class="catalog_item__name">{{[product_data.name]}}</p>
        <p class="catalog_item__price">{{product_data.price}} P</p>
        <button 
        class="v-catalog-item__add_to_cart_btn btn" 
        @click="addToCart">
        Add to cart
        </button>
    </div>
</template>

<script>
export default {
    name: "v-catalog-item",
    props: {
        product_data: {
            type: Object,
            default() {
                return {}
            }
        }
    },
    data() {
        return {

        }
    },
    computed: {},
    methods: {
        addToCart() { // пробрасывает карточку товара в v-catalog
            this.$emit('addToCart', this.product_data);
        }
    },
    mounted() {
        this.$set(this.product_data, 'quantity', 1); // $set - внутренний метод vue, которые добавляет ключ к элементу
    } 
}
</script>

<style lang="scss">
  .v-catalog-item {
    flex-basis: 25%;
    box-shadow: 0 0 8px #e0e0e0;
    padding: $padding*2;
    margin-bottom: $margin*2;
  &__image {
      width: 120px;
  }
  }

</style>
