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
                <product-category-row
                    :key="product.category" 
                    :category="product.category"
                    v-if="product.category !== products[index > 0 ? (index - 1) : 0].category">
                </product-category-row>
                <product-row :key="product.name" :product="product"></product-row>
            </template>
        </tbody>
    </table>
</template>

<script>
import ProductCategoryRow from './ProductCategoryRow.vue'
import ProductRow from './ProductRow'

export default {
    props: ['products'],
    
    components: {
        ProductCategoryRow,
        ProductRow
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