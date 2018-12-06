<template>
    <form>
        <input type="text" placeholder="Search..."
            @input="handleFilterTextInput" />
        <p>
            <label>
                <input type="checkbox"
                    @change="handleInStockeChange" />
                {{' '}}
                Only show products in stock
            </label>
        </p>
    </form>
</template>

<script>
export default {
    props: ['filterText', 'inStockOnly'],

    methods: {
        handleFilterTextInput (e) {
            this.$emit('onFilterTextInput', e.target.value)
        },
        handleInStockeChange (e) {
            this.$emit('onInStockeChange', e.target.value)
        }
    }
}
</script>