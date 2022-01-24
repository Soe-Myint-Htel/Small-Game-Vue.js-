<template>
    <div v-if="score <= 250">
        <p>OMG! You are too fast</p>
    </div>
    <div v-else-if="score > 250 && score < 500">
        <p>Hum...You are normal</p>
    </div>
    <div v-else>
        <p>You are too slow :(</p>
    </div>
</template>

<script>
export default {
    props : ['score']
}
</script>

<style>

</style>