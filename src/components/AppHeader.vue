<template>
    <div class="main">
        <h1>VueShop!</h1>
        <div class="button-div">
            <router-link to="/signin">Sign In</router-link>
            <router-link to="/products">Products</router-link>
            <router-link to="/cart">Cart<span class="count">{{ count }}</span></router-link>
        </div>
    </div>
</template>

<script>
export default {
    computed: {
        count() {
            return this.$store.getters.totalCount;
        }
    }
}
</script>

<style scoped> 
.main {
    padding: 10px 10px;
    font-family: Arial, Helvetica, sans-serif;
    background-color: #05386B;
    display: flex;
   justify-content: space-between;
}

h1 {
    font-size: 55px;
    display: inline-block;
    color: #EDF5E1;
}

a {
    display: inline-block;
    background-color: #5CDB95;
    padding: 10px 5px;
    width: 100px;
    height: 45px;
    color: #EDF5E1;
    font-size: 20px;
    border-style: none;
    cursor: pointer;
    border-radius: 10px;
    text-decoration: none;
    margin-left: 20px;
    box-shadow: 0 2px 8px #032241;
    outline: none;
}

a:hover {
    opacity: 80%;
}

.button-div {
    margin: auto 0px;
    display: inline-block;
    align-items: center;
    text-align: center;
}

.count {
    height: 25px;
    width: 25px;
    display: inline-block;
    background-color: #05386B;
    color: #EDF5E1;
    margin-left: 5px;
    border-radius: 50%;
    padding: 5px;
    font-size: 15px;
}
</style>