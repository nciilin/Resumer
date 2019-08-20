<template>
  <div>
    <h2>联系方式</h2>
    <el-form>
      <div class="container" v-for="(contactMessage, index) in contacts">
        <el-form-item label="手机">
          <el-input v-model="contactMessage.contact"></el-input>
        </el-form-item>
        <el-form-item label="邮箱">
          <el-input v-model="contactMessage.content"></el-input>
        </el-form-item>
        <button class="remove" v-on:click="removeContactHistory(index)">
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-Remove" />
          </svg>
        </button>
        <hr />
      </div>
      <button class="add" v-on:click="addContactHistory">
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-add" />
        </svg>
      </button>
    </el-form>
  </div>
</template>

<script>
export default {
  props: ["contacts"],
  methods: {
    addContactHistory() {
      this.contacts.push({
        name: "",
        content: ""
      });
    },
    removeContactHistory(index) {
      this.contacts.splice(index, 1);
    }
  }
};
</script>