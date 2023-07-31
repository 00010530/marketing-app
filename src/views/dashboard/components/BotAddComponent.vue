<template>
  <section class="botAdd">
    <el-upload
      class="avatar-uploader"
      action="https://run.mocky.io/v3/9d059bf9-4660-45f2-925d-ce80ad6c4d15"
      :show-file-list="false"
      :on-success="handleAvatarSuccess"
      :before-upload="beforeAvatarUpload"
    >
      <img v-if="imageUrl" :src="imageUrl" class="avatar" />
      <el-icon v-else class="avatar-uploader-icon"><Plus /></el-icon>
    </el-upload>
    <form class="form">
      <label for="mavzu">Mavzu:</label>
      <input type="text" placeholder="Nomi" />
      <label for="">Filial:</label>
      <el-select
        v-model="activeBranch"
        class="m-2"
        placeholder="Select"
        size="large"
      >
        <el-option
          v-for="item in allBranches"
          :key="item.value"
          :label="item.label"
          :value="item.value"
        />
      </el-select>
      <label for="message">Text</label>
      <textarea
        name=""
        id=""
        cols="30"
        rows="10"
        placeholder="Ma'lumot"
      ></textarea>
    </form>

    <div class="bot-add-footer">
      <div class="bot-add-btns">
        <button class="cancel">Cancel</button>
        <button class="done" @click="doneBtnClick()">Done</button>
      </div>
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
import { ref } from "vue";
import { ElMessage } from "element-plus";
import { Plus } from "@element-plus/icons-vue";

export default {
    emits: ["marsBot"],
  setup(_, { emit }) {
    const imageUrl = ref("");
    const value = ref("");

    const doneBtnClick = () => {
      emit("marsBot");
    };

    const handleAvatarSuccess = (response, uploadFile) => {
      imageUrl.value = URL.createObjectURL(uploadFile.raw);
    };
    const beforeAvatarUpload = (rawFile) => {
      if (rawFile.type !== "image/jpeg") {
        ElMessage.error("Avatar picture must be JPG format!");
        return false;
      } else if (rawFile.size / 1024 / 1024 > 2) {
        ElMessage.error("Avatar picture size can not exceed 2MB!");
        return false;
      }
      return true;
    };

    const allBranches = [
      {
        label: "Tinchlik",
        value: 1,
      },
      {
        label: "Yunusobod",
        value: 2,
      },
      {
        label: "Qutbiniso",
        value: 3,
      },
      {
        label: "Parlament",
        value: 4,
      },
    ];

    return { handleAvatarSuccess, beforeAvatarUpload, value, allBranches, Plus, doneBtnClick };
  },
};
</script>

<style>
.botAdd {
  color: #000;
  width: 400px;
  border-radius: 20px;
  border: 0.2px #a5a9bc solid;
}

.form {
  display: flex;
  flex-direction: column;
  background-color: #f8f8f8;
}

.form label {
  font-size: 16px;
  font-family: Inter;
  font-weight: 600;
}

.form input {
  padding: 6px 20px;
  border: 0.2px #c6cad3 solid;
  border-radius: 6px;
  outline: none;
  background-color: #f8f8f8;
  color: #D9D9D9;
}

.form label,
input {
  margin: 5px 71px 5px 23px;
}

.form .el-select {
  margin: 5px 71px 5px 23px;
}

.form textarea {
  border-top: 0.2px #c6cad3 solid;
  border-right: none;
  border-left: none;
  border-bottom: none;
  border-radius: 6px;
  background: none;
  outline: none;
  padding: 10px;
}

.bot-add-footer{
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #f8f8f8;
    padding: 14px 18px;
}

.bot-add-btns button {
  border: none;
  padding: 7px 23px;
  border-radius: 8px;
  cursor: pointer;
}

.bot-add-btns .cancel {
  margin-right: 10px;
}

.form .el-input__wrapper {
  background-color: #f8f8f8;
}

.avatar-uploader .el-upload {
  border: none;
  border-radius: 6px;
  cursor: pointer;
  position: relative;
  overflow: hidden;
  transition: var(--el-transition-duration-fast);
  display: flex;
  justify-content: center;
  align-items: center;
  background-image: url("../../../assets/add-photo.png");
  background-repeat: no-repeat;
  background-position: center;
}

.avatar-uploader .el-upload:hover {
  border-color: var(--el-color-primary);
}

.el-icon.avatar-uploader-icon {
  font-size: 28px;
  color: #8c939d;
  height: 242px;
  text-align: center;
}

.bot-add-footer .block {
  width: 30px;
}
</style>