<template>
  <header-component />
  <main class="main">
    <sidebar-component />
    <section class="board">
      <div class="wrapper">
        <div class="wrapper-left">
          <bot-component @marsBotDetail="getClickedEvent('botDetails')" @marsBotAdd="getClickedEvent('bot-add')"/>
          <div class="bottom">
            <products-component @addProduct="getClickedEvent('add-product')"/>
            <news-component />
          </div>
        </div>
        <div class="wrapper-right">
          <div class="heading">
              <label for="branch">Branch</label>
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
          </div>
          <!-- <social-component /> -->
          <component :is="activeComponent + '-component'" @marsBot="getClickedEvent('social')" /> 
        </div>
      </div>
    </section>
    
  </main>
</template>

<script>
export default {
  data() {
    return {
      activeBranch: null,
      allBranches: [
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
      ],
      activeComponent: 'social'
    };
  },
  methods: {
    getClickedEvent(val) {
      this.activeComponent = val
    }
  }
};
</script>

<style>
.main {
  width: 100vw;
  display: flex;
  justify-content: space-between;
  margin-top: 105px;
}

.board {
  margin-left: 84px;
  padding: 30px 55px;
  width: 100%;
}

.wrapper {
  display: flex;
  justify-content: center;
  gap: 71px;
}

.heading {
  padding-bottom: 42px;
}

.heading label {
  color: #17233b;
  font-size: 20px;
  font-weight: 700;
  margin-right: 4px;
  border-right: 1px #E3391B solid;
  padding: 0 10px;
}

.heading .el-input__wrapper {
  box-shadow: none;
}

.heading .el-input__wrapper:hover {
  box-shadow: none;
}

.bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 72px;
}
</style>