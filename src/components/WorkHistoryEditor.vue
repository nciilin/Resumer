<template>
  <div>
    <h2>工作经历</h2>
    <el-form>
      <div class="container" v-for="(work, index) in workHistory">
        <el-form-item label="公司">
          <el-input v-model="work.company"></el-input>
        </el-form-item>
        <el-form-item label="内容">
          <el-input v-model="work.content"></el-input>
        </el-form-item>
        <button class="remove" v-on:click="remvoeWorkHistory(index)">
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-Remove" />
          </svg>
        </button>
        <hr />
      </div>
      <button class="add" v-on:click="addWorkHistory">
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-add" />
        </svg>
      </button>
    </el-form>
  </div>
</template>

<script>
export default {
  props: ["workHistory"],
  methods: {
    addWorkHistory() {
      this.workHistory.push({
        company: "",
        content: ""
      });
    },
    remvoeWorkHistory(index) {
      this.workHistory.splice(index, 1);
    }
  }
};
</script>
