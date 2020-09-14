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
                greeting: 'Hello Meteor, from Vue',
            };
        },
    };
</script>

<style lang="css" scoped>
.text-color{
    color:rgb(2, 128, 19);
}
</style>