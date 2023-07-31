<template>
    <section class="news-section">
        <div class="news">
            <h1>News</h1>
        <div class="news-cards">
            <div class="news-card">
                <a href="#"><img src="../../../assets/news1.png" alt=""></a>
            </div>
            <div class="news-card">
                <a href="#"><img src="../../../assets/news1.png" alt=""></a>
            </div>
            <div class="news-card">
                <a href="#"><img src="../../../assets/news1.png" alt=""></a>
            </div>
            <div class="news-card">
                <a href="#"><img src="../../../assets/news1.png" alt=""></a>
            </div>
            <div class="news-card">
                <a href="#"><img src="../../../assets/news1.png" alt=""></a>
            </div>
        </div>
        </div>
        <div class="card-footer">
      <p>Yangi Maxsulot qo'shish</p>
      <el-button>+ Add</el-button>
    </div>
    </section>
</template>
<script>
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