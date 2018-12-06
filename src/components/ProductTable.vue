<template>
    <table>
        <thead>
            <tr>
                <th>Name</th>
                <th>Price</th>
            </tr>
        </thead>
        <tbody>
            <template v-for="(product, index) in products">
                <template v-if="product.name.toLowerCase().indexOf(filterText.toLowerCase()) !== -1">
                    <product-category-row
                        :key="product.category" 
                        :category="product.category"
                        v-if="showCategory(product, index)">
                    </product-category-row>
                    <product-row
                        v-if="(inStockOnly && product.stocked) || !inStockOnly"
                        :key="product.name"
                        :product="product"
                    ></product-row>
                </template>
            </template>
        </tbody>
    </table>
</template>

<script>
import ProductCategoryRow from './ProductCategoryRow.vue'
import ProductRow from './ProductRow'

export default {
    props: ['products', 'filterText', 'inStockOnly'],
    
    components: {
        ProductCategoryRow,
        ProductRow
    },

    computed: {
        _products (products) {

        }
    },

    methods: {
        showCategory (product, index) {
            return product.category !== this.products[index > 0 ? (index - 1) : 0].category
        }
    }
}
</script>

<style>
table {
    border-collapse: collapse;    
}

table td, table th{
    border: 1px solid #ccc;
}
</style>