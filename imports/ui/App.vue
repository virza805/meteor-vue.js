<template>
    <div>
        <p class="text-color">
            {{ greeting }}
        </p>

        <temp-component/>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                greeting: 'This is my first work using Meteor + vue.js + MongoDB.',
            };
        },
    };
</script>

<style lang="css" scoped>
.text-color{
    color:#b8060f;
    text-align: center;
}
</style>