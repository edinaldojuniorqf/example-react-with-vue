<template>
    <div>
        <search-bar
            :filterText="filterText"
            :inStockOnly="inStockOnly"
            @onFilterTextInput="handleFilterTextInput"
            @onInStockeChange="handleInStockeChange">
        </search-bar>
        
        <product-table
            :products="products"
            :filterText="filterText"
            :inStockOnly="inStockOnly">
        </product-table>
    </div>
</template>

<script>
import SearchBar from './SearchBar'
import ProductTable from './ProductTable'

export default {
    props: ['products'],

    data () {
      return {
        filterText: '',
        inStockOnly: false
      }
    },
    
    components: {
        ProductTable,
        SearchBar
    },

    methods: {
        handleFilterTextInput (value) {
            this.filterText = value
        },
        handleInStockeChange (value) {
            this.inStockOnly = value
        }
    }
}
</script>