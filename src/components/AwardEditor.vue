<template>
  <div>
    <h2>获奖经历</h2>
    <el-form>
      <div class="container" v-for="(award, index) in awards">
        <el-form-item label="获奖">
          <el-input v-model="award.name"></el-input>
        </el-form-item>
        <el-form-item label="内容">
          <el-input v-model="award.content"></el-input>
        </el-form-item>
        <button class="remove" v-on:click="removeAwardHistory(index)">
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-Remove" />
          </svg>
        </button>
        <hr />
      </div>
      <button class="add" v-on:click="addAwardHistory">
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-add" />
        </svg>
      </button>
    </el-form>
  </div>
</template>

<script>
export default {
  props: ["awards"],
  methods: {
    addAwardHistory() {
      this.awards.push({
        name: "",
        content: ""
      });
    },
    removeAwardHistory(index) {
      this.awards.splice(index, 1);
    }
  }
};
</script>