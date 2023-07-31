<template>
  <section class="products-section">
    <div class="products">
    <h1>Products</h1>
    <div class="cards">
      <div class="card" v-for="product in products" v-bind:key="product.id">
        <div class="card-img">
          <img v-bind:src="product.img" alt="" />
        </div>
        <div class="card-text">
          <h2>{{ product.name }}</h2>

          <div class="coins">
            <img src="../../../assets/coin.svg" alt="" />
            <p>{{ product.coins }} Coins</p>
          </div>
        </div>
        <div class="card-btns">
          <img src="../../../assets/edit.png" alt="" />
          <p>{{ product.ostatok }} остаток</p>
        </div>
      </div>
    </div>
    
</div>
  <div class="card-footer">
      <p>Yangi Maxsulot qo'shish</p>
      <el-button @click="addProductBtnClick()">+ Add</el-button>
    </div>
  </section>
</template>

<script>
import { ref } from "vue";

export default {
  emits: ['addProduct'],
  setup(_, {emit}) {
    const products = ref({ activity: "" });


    function theData(url) {
  fetch(url)
    .then((response) => response.json())
    .then((actualData) => {
      console.log(actualData);
      products.value = actualData;
    })
    .catch((e) => {
      console.error("Error: ", e);
    });

  return products;
}

const addProductBtnClick = () => {
      emit('addProduct')
    }

theData("http://localhost:3000/products");

return {
  products, addProductBtnClick
}
  }
}


</script>

<style scoped>
.products-section {
    width: 50%;
}
.products {
  width: 100%;
  padding: 21px 24px;
  border: 0.5px #a5a9bc solid;
  border-radius: 10px 10px 0 0;
  height: 514px;
  overflow-y: scroll;
}

.products h1 {
  color: #17233b;
  font-size: 30px;
  font-family: Inter;
  font-weight: 500;
}

.products::-webkit-scrollbar {
  display: none; /* Safari and Chrome */
}

.card {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 24px 0;
}

.card-img img {
  width: 84px;
  border-radius: 20px;
  border: 0.4px solid #c6cad3;
}

.card-text {
  width: 150px;
}

.card-text h2 {
  font-size: 18px;
  padding-bottom: 18px;
}

.coins {
  display: flex;
  align-items: center;
  gap: 1px;
}

.card-text p {
  font-size: 14px;
}

.card-btns {
  display: flex;
  flex-direction: column;
  align-items: end;
}

.card-btns p {
  font-size: 8px;
  padding-top: 24px;
}

.card-footer {
  background-color: #e3391b;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 19px;
  margin-bottom: 0;
  width: 100%;
  border-radius: 0 0 10px 10px;
}

.card-footer p {
  color: #fff;
  font-size: 20px;
  font-family: Gilroy;
  font-weight: 500;
}

.card-footer .el-button {
  box-shadow: 0px 0px 2px 1px rgba(0, 0, 0, 0.25);
  margin: 5px;
  border-radius: 7px;
  color: #17233b;
}
</style>