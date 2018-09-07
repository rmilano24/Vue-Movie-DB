<template>
    <header>
        <h1><router-link to="/">{{ title }}</router-link></h1>
    </header>
</template>

<script>
    export default {
        name: "Header",
        props: {
            title: String
        },
        data() {
            return {
                show: false,
                name: 'Ryan'
            };
        },
    };
</script>

<style scoped>
header {
    background-color: #111;
    padding: 20px;
    color: #fff;
}
h1 {
    margin: 0px;
}


/* name-enter -> name-enter-to */
/* name-enter-active */

/* name-leave -> name-leave-to */
/* name-leave-active */

</style>