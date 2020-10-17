<template>
<transition>
    <div class="main">
        <div class="top">
            <h3>{{ extendTitle }}</h3>
            <img :src="imagePath">
            <h3>{{ extendTitle }}</h3>
            <p class="price">{{ price }}</p>
        </div>
        <button @click="addProduct">Buy!</button>
    </div>
</transition>
</template>

<script>
export default {
    props: ['count', 'id', 'title', 'price', 'desc', 'image'],
    data() {
        return {
            longTitle: this.title,
        }
    },
    computed: {
        imagePath() {
            return this.image;
        },
        extendTitle() {
            let title = this.longTitle;
            for(let i=0; i<50; i++) {
                title = title + ' ' + this.longTitle;
            }
            return title;
        }
    },
    methods: {
        addProduct() {
            if(this.id === 'article1'){
                this.$store.state.articles[0].count++;
            }
            if(this.id === 'article2'){
               this.$store.state.articles[1].count++;
            }
            if(this.id === 'article3'){
               this.$store.state.articles[2].count++;
            }
        }
    }
}
</script>

<style scoped>
h3 {
    margin: auto 0px;
    white-space: nowrap;
    animation: scroller 20s linear infinite;
}

.main {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    background-color: #EFEFEF;
    border: none;
    border-radius: 10px;
    display: inline-block;
    text-align: center;
    width: 23%;
    animation: loadit 0.5s ease-in;
    overflow: hidden;
}

.top {
    padding: 5px;
}

button {
    background-color: #5CDB95;
    padding: 10px 5px;
    font-size: 20px;
    border-style: none;
    cursor: pointer;
    color: #EDF5E1;
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    width: 100%;
}

button:hover {
    opacity: 80%;
}

.price {
    display: inline-block;
    color: #EDF5E1;
    width: 100%;
    background-color: #05386B;
    padding: 3px 0px;
}

@keyframes loadit {
    0% {
        opacity: 0%;
        transform: translateY(40px);
    }
    100% {
        opacity: 100%;
        transform: translateY(0);
    }
}

@keyframes scroller {
    0% {
        transform: translateX(-1000px);
    }
    100% {
        transform: translateX(-10px);
    }
}
</style>