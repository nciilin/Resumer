<template>
  <div class="ResumePreview">
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
  name: "ResumePreview"
};
</script>

<style lang="scss">
.ResumePreview {
  ul {
    margin-left: 50%;
    margin-top: 30px;
    border: 1px solid red;
    background: #ffffff;
    height: 680px;
    li {
      list-style: none;
    }
  }
}
</style>