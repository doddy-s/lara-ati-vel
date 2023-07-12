<script>
    export default {
        created() {
            setTimeout( () => this.$router.push({ path: '/home'}), 1000);
        },
    }
</script>

<template>
    <div>
        <h1>Splash Page</h1>
    </div>
</template>