<template>
  <div class="ResumeEditor">
    <ul>
      <li>tab1</li>
      <li>tab2</li>
      <li>tab3</li>
      <li>tab4</li>
      <li>tab5</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ResumeEditor"
};
</script>

<style lang="scss">
.ResumeEditor {
  ul {
    float: left;
    margin-top: 30px;
    border: 1px solid red;
    width: 45%;
    height: 680px;
    background: #ffffff;
    li {
      list-style: none;
    }
  }
}
</style>