<template>
    <footer id="footer">
        <p>Make Your Burger &copy; 2021</p>
    </footer>
</template>

<script>
    export default {
        name: "Footer"
    }
</script>

<style scoped>
#footer {
    height: 200px;
    background-color: rgb(242, 247, 241);
    border-top: 4px solid #111;
    color: rgb(56, 33, 2); /*rgb(8, 68, 40);*/
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
}
</style>