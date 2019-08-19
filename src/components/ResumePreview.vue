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
    margin-left: 40%;
    margin-top: 45px;
    height: 400px;
    background: #ffffff;
    box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.25);
    li {
      list-style: none;
    }
  }
}
</style>