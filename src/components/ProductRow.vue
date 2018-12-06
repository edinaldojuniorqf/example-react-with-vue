<template>
    <tr>
        <td>
            <span :style="product.stocked ? '' : {color: 'red'}">
                {{ product.name }}
            </span>
        </td>
        <td>{{ product.price }}</td>
    </tr>
</template>

<script>
export default {
    props: ['product']
}
</script>

<style>

</style>
