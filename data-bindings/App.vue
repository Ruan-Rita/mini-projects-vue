<template>
    <div :style="{backgroundColor: backgroundColor}">
        Ruan Rita {{name}}
        <input type="text" v-model="name" >
    </div>
</template>

<script>
export default {
    data: () => ({
        name: 'COD-Ruan',
        backgroundColor: "#FFF712"
    })
}
</script>

<style>

</style>