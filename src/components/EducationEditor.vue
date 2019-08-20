<template>
  <div>
    <h2>学习经历</h2>
    <el-form>
      <div class="container" v-for="(study, index) in education">
        <el-form-item label="学校">
          <el-input v-model="study.school"></el-input>
        </el-form-item>
        <el-form-item label="内容">
          <el-input v-model="study.content"></el-input>
        </el-form-item>
        <button class="remove" v-on:click="removeStudyHistory(index)">
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-Remove" />
          </svg>
        </button>
        <hr />
      </div>
      <button class="add" v-on:click="addStudyHistory">
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-add" />
        </svg>
      </button>
    </el-form>
  </div>
</template>

<script>
export default {
  props: ["education"],
  methods: {
    addStudyHistory() {
      this.education.push({
        school: "",
        content: ""
      });
    },
    removeStudyHistory(index) {
      this.education.splice(index, 1);
    }
  }
};
</script>