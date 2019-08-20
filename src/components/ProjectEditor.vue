<template>
  <div>
    <h2>个人项目</h2>
    <el-form>
      <div class="container" v-for="(project, index) in projects">
        <el-form-item label="个人项目">
          <el-input v-model="project.name"></el-input>
        </el-form-item>
        <el-form-item label="详情">
          <el-input v-model="project.content"></el-input>
        </el-form-item>
        <button class="remove" v-on:click="removeProjectHistory(index)">
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-Remove" />
          </svg>
        </button>
        <hr />
      </div>
      <button class="add" v-on:click="addProjectHistory">
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-add" />
        </svg>
      </button>
    </el-form>
  </div>
</template>

<script>
export default {
  props: ["projects"],
  methods: {
    addProjectHistory() {
      this.projects.push({
        name: "",
        content: ""
      });
    },
    removeProjectHistory(index) {
      this.projects.splice(index, 1);
    }
  }
};
</script>