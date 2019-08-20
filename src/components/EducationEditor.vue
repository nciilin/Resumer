<template>
  <div>
    <h2>学习经历</h2>
    <el-form>
      <div class="container" v-for="(item, index) in education">
        <el-form-item label="学校">
          <el-input v-model="item.school"></el-input>
        </el-form-item>
        <el-form-item label="学位">
          <el-input v-model="item.degree"></el-input>
        </el-form-item>
        <el-form-item label="时间">
          <el-input v-model="item.duration"></el-input>
        </el-form-item>
        <button class="remove" v-on:click="removeItem(index)">
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-Remove" />
          </svg>
        </button>
        <hr />
      </div>
      <button class="add" v-on:click="addItem">
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
    addItem() {
      this.education.push({
        school: "",
        degree: "",
        duration: ""
      });
    },
    removeItem(index) {
      this.education.splice(index, 1);
    }
  }
};
</script>