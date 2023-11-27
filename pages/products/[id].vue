<template>
    <div>
        <ProductDetails :product="product" />
    </div>
</template>

<script setup lang="ts">
import { useRoute } from 'vue-router'
definePageMeta({
    layout: 'products'
})
const { id } = useRoute().params

const { data: product } = await useFetch('https://fakestoreapi.com/products/' + id,)
if (!product.value) {
    throw createError({
        statusCode: 404,
        statusMessage: 'Product not found',
        fatal: false
    })
}

</script>

<style scoped></style>