<template>
    <div class="container">
        <h1>Payment</h1>
        <input v-on:input="inputName1" />
        <input v-on:input="inputPrice1" />
        <input v-on:input="inputName2" />
        <input v-on:input="inputPrice2" />
        <div class="payment">
            <label>{{ Item1.name }}</label>
            <label>{{ Item1.price }} yen</label>
            <a v-bind:href="url1">bought at...</a>
            <button v-on:click="buy(Item1.name)">BUY</button>
        </div>
        <div class="payment">
            <label>{{ Item2.name }}</label>
            <label>{{ Item2.price }} yen</label>
            <a v-bind:href="url1">bought at...</a>
            <button v-on:click="buy(Item2.name)">BUY</button>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'

const Item1 = reactive({
    name: null,
    price: null,
});

const Item2 = reactive({
    name: null,
    price: null,
});

// const ItemName1 = ref<string>('Desk');
const ItemName2 = 'Bike';

// const ItemPrice1 = '40000';
const ItemPrice2 = '20000';

const url1 = 'https://www.amazon.co.jp/Jiandi-%E3%82%B2%E3%83%BC%E3%83%9F%E3%83%B3%E3%82%B0%E3%83%87%E3%82%B9%E3%82%AF-%E3%83%91%E3%82%BD%E3%82%B3%E3%83%B3%E3%83%87%E3%82%B9%E3%82%AF-%E3%83%A9%E3%83%83%E3%82%AF%E4%BB%98%E3%81%8D%E3%83%87%E3%82%B9%E3%82%AF-%E3%82%AA%E3%83%95%E3%82%A3%E3%82%B9%E3%83%87%E3%82%B9%E3%82%AF/dp/B0B3Y9KXCS/ref=sr_1_5?__mk_ja_JP=%E3%82%AB%E3%82%BF%E3%82%AB%E3%83%8A&crid=9XSA60HQD2J2&keywords=desk&qid=1700574894&sprefix=desk,aps,172&sr=8-5&th=1'

const buy = (itemName: string) => {
    alert('Are you sure to buy ' + itemName + '?');
}

// const input = (event: any) => {
//     console.log('event:', event.target.value);
//     ItemName1.value = event.target.value;
// }

const inputName1 = (event: any) => {
    console.log('event:', event.target.value);
    Item1.name = event.target.value;
}

const inputPrice1 = (event: any) => {
    console.log('event:', event.target.value);
    Item1.price = event.target.value;
}

const inputName2 = (event: any) => {
    console.log('event:', event.target.value);
    Item2.name = event.target.value;
}

const inputPrice2 = (event: any) => {
    console.log('event:', event.target.value);
    Item2.price = event.target.value;
}
</script>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.payment {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 80px;
    width: 400px;
    background-color: rgb(160, 160, 231);
    margin-bottom: 8px;
}

label {
    font-size: 20px;
    font-weight: bold;
}
</style>
