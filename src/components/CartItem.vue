<template>
    <div class="main" v-if="!checkCount">
        <img :src="imagePath" class='image'>
        <h3>{{ title }}</h3>
        <div>
            <button @click="minus" class="tick">-</button>
            <span>{{ count }}</span>
            <button @click="plus" class="tick">+</button>
        </div>
        <p>{{ price }}</p>
        <button @click="remove" class="remove">Remove</button>
    </div>
</template>

<script>
export default {
    props: ['count', 'id', 'title', 'price', 'desc', 'image'],
    methods: {
        plus() {
            if(this.id === 'article1'){
                this.$store.state.articles[0].count++;
            }
            if(this.id === 'article2'){
               this.$store.state.articles[1].count++;
            }
            if(this.id === 'article3'){
               this.$store.state.articles[2].count++;
            }
        },
        minus() {
            if(this.id === 'article1'){
                this.$store.state.articles[0].count--;
            }
            if(this.id === 'article2'){
               this.$store.state.articles[1].count--;
            }
            if(this.id === 'article3'){
               this.$store.state.articles[2].count--;
            }
        },
        remove() {
            if(this.id === 'article1'){
                this.$store.state.articles[0].count = 0;
            }
            if(this.id === 'article2'){
               this.$store.state.articles[1].count = 0;
            }
            if(this.id === 'article3'){
               this.$store.state.articles[2].count = 0;
            }
        }
    },
    computed: {
        checkCount() {
            return this.count === 0;
        },
        imagePath() {
            return this.image;
        },
    }
}
</script>

<style scoped>
.image {
    border-bottom: solid 1px black;
}

.main {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    background-color: #EFEFEF;
    padding: 10px;
    border: none;
    border-radius: 10px;
    width: 50%;
    max-width: 500px;
}

span {
    display: inline-block;
    width: 30px;
}

.tick {
    background-color: #CDCDCD;
    color: white;
    padding: 10px 5px;
    font-size: 20px;
    border-style: none;
    cursor: pointer;
    width: 30px;
}

.remove {
    background-color: #5CDB95;
    padding: 10px 5px;
    font-size: 20px;
    border-style: none;
    cursor: pointer;
    color: #EDF5E1;
    border-radius: 10px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
}

div, p {
    margin-top: 5px;
}
</style>