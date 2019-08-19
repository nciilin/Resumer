<template>
  <div class="page clearfix">
    <header>
      <ResumeLeftBar />
    </header>
    <main>
      <ResumeSearch />
    </main>
    <footer>
      <ResumePreview />
    </footer>
  </div>
</template>

<script>
import "normalize.css/normalize.css";
import "./assets/reset.css";
import ResumeLeftBar from "./components/ResumeLeftBar";
import ResumeSearch from "./components/ResumeSearch";
import DisplayBoard from "./components/DisplayBoard";
import ResumePreview from "./components/ResumePreview";

export default {
  name: "App",
  components: { ResumeLeftBar, ResumeSearch,DisplayBoard, ResumePreview }
};
</script>

<style lang="scss">
.clearfix {
  content: "";
  display: block;
  clear: both;
}
.icon {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}
.page {
  font-family: 12px/1.5 Tahoma, Helvetica, Arial, "宋体", sans-serif;
  header {
    max-width: 15%;
    float: left;
  }
  main {
    margin-left: 150px;
  }
  footer {
    margin-top: 32px;
    margin-left: 240px;
    background: #FDFEFF;
  }
}
</style>
