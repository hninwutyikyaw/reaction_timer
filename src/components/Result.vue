<template>
    <h1>Result is {{score}}ms</h1>
    <div v-if="score<250">You are too fast</div>
    <div v-else-if="score>250 && score<500">You are normal</div>
    <div v-else>You are too slow.Try again</div>


</template>

<script>
export default {
    props:['score']
}
</script>

<style>

</style>