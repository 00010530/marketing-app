<template>
  <section class="news-section">
    <div class="news">
      <h1>News</h1>
      <div class="news-cards">
        <div class="news-card" v-for="item in news" v-bind:key="item.id">
          <a href="#"><img v-bind:src="item.img" /></a>
          <div class="news-description">
            <p>{{ item.description }}</p>
          </div>
        </div>
      </div>
    </div>
    <div class="card-footer">
      <p>Yangilik qo'shish</p>
      <el-button>+ Add</el-button>
    </div>
  </section>
</template>
<script>
import { ref } from "vue";

export default {
  setup() {
    const news = ref({ activity: "" });

    function theData(url) {
      fetch(url)
        .then((response) => response.json())
        .then((actualData) => {
          console.log(actualData);
          news.value = actualData;
        })
        .catch((e) => {
          console.error("Error: ", e);
        });

      return news;
    }

    theData("http://localhost:3000/news");

    return {
      news,
    };
  },
};
</script>

<style>
.news-section {
  width: 50%;
}
.news {
  width: 100%;
  padding: 21px 24px;
  border: 0.5px #a5a9bc solid;
  border-radius: 10px 10px 0 0;
  height: 514px;
  overflow-y: scroll;
}

.news-cards {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.news::-webkit-scrollbar {
  display: none; /* Safari and Chrome */
}

.news h1 {
  color: #17233b;
  font-size: 30px;
  font-family: Inter;
  font-weight: 500;
  margin-bottom: 25px;
}

.news-card {
  margin: 15px 0;
  position: relative;
}

.news-card img {
  width: 326px;
  height: 110px;
  object-fit: cover;
  object-position: 20% 15%;
  border: 0.20px #E3391B solid;
  border-radius: 5px;
}

.news-description {
  width: 100%;
  height: 27px;
  position: absolute;
  bottom: 4px;
  background: rgba(0, 0, 0, 0.6);
  padding-left: 20px;
  padding-top: 4px;
}

.news-description p {
  width: 165px;
  color: #fff;
  font-size: 8px;
  font-family: Gilroy;
  font-weight: 500;
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