<template>
  <div class="ResumeEditor">
    <ul>
      <li v-bind:class="{active: currentTab === 0}">tab1</li>
      <li v-bind:class="{active: currentTab === 1}">tab2</li>
      <li v-bind:class="{active: currentTab === 2}">tab3</li>
      <li v-bind:class="{active: currentTab === 3}">tab4</li>
      <li v-bind:class="{active: currentTab === 4}">tab5</li>
      <li v-bind:class="{active: currentTab === 5}">tab6</li>
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
    width: 35%;
    height: 680px;
    background: #ffffff;
    box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.25);
    li {
      list-style: none;
    }
  }
}
</style>