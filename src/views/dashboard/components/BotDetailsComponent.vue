<template>
  <section class="bot-details">
    <img src="../../../assets/botDetail.png" alt="" />
    <p>
      😋 «Mars IT School»da mazali ziyofat! 🍕 Kelayotgan yakshanba 23-iyul kuni
      barcha o'quvchilarimizni «Pizza time» ziyofatiga taklif qilib qolamiz. 😉
      Dam olish kuningizni mazali pitsa bilan o'tkazing. 📆 O'tkazilish kuni:
      23-iyul/yakshanba ⏰ Vaqti: 11:00 📍 Manzil: Tinchlik filiali
      @Mars_tinchlik) 👉🏻Joylar soni cheklangan 👏🏻Eventga yozilishga ulgurib
      qoling «Mars IT School» — bu kelajak! 📞 78-777-77-57
    </p>

    <div class="bot-details-btns">
      <button class="cancel">Cancel</button>
      <button class="done" @click="doneBtnClick()">Done</button>
      <button class="send">Send</button>
      <div class="block">
        <el-date-picker
          v-model="value1"
          type="datetime"
          :default-value="new Date()"
        />
      </div>
    </div>
  </section>
</template>

<script>

export default {
  emits: ["marsBot"],
  setup(_, { emit }) {
    const doneBtnClick = () => {
      emit("marsBot");
    };
    return {
      doneBtnClick,
    };
  },
};
</script>

<style>
.bot-details {
  color: #000;
  width: 400px;
  padding: 28px 38px;
  border-radius: 20px;
  border: 0.2px #a5a9bc solid;
}

.bot-details p {
  width: 285px;
}

.bot-details-btns {
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.bot-details button {
  padding: 7px 22px;
  border: none;
  border-radius: 8px;
  text-align: center;
  font-size: 12px;
  font-family: Gilroy;
  font-weight: 400;
}

.cancel {
  background-color: #e3391b;
  color: #fff;
}

.done {
  background-color: #d9d9d9;
  color: #17233b;
}

.send {
  background-color: #17233b;
  color: #fff;
}

.bot-details .block {
  width: 30px;
  margin: 30px;
}
</style>