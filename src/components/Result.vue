<template>
    <div v-if="score<100">
        <h1>
            Good Speed!
        </h1>
    </div>
    <div v-else-if="score>100 && score<300">
        <h1>Nice catch man! Great!</h1>
    </div>
    <div v-else-if="score>300 && score<800">
        <h1>It's just normal speed. Try to catch faster </h1>
    </div>
    <div v-else>
        <h1>
            Too slow man! Try again
        </h1>
    </div>
    <p>Result is: {{score}}ms</p>
</template>

<script>
export default {
    props:["score"]
}
</script>

<style>

</style>