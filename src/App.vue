<template>
  <div class="page clearfix" v-bind:class="{previewMode: previewMode}">
    <header id="leftBar">
      <ResumeLeftBar v-bind:resume="resume" />
    </header>
    <main id="search">
      <ResumeSearch v-on:preview="preview" />
    </main>
    <footer id="preview">
      <ResumePreview v-bind:resume="resume" />
    </footer>
    <button id="exitPreview" v-on:click="exitPreview">
      <svg class="icon">
        <use xlink:href="#icon-Remove" />
      </svg>退出
    </button>
  </div>
</template>

<script>
import "normalize.css/normalize.css";
import "./assets/reset.css";
import ResumeLeftBar from "./components/ResumeLeftBar";
import ResumeSearch from "./components/ResumeSearch";
import ResumePreview from "./components/ResumePreview";

export default {
  name: "App",
  data() {
    return {
      previewMode: false,
      resume: {
        profile: { name: "", city: "", birth: "" },
        workHistory: [{ company: "", content: "" }],
        education: [{ school: "", degree: "", duration: "" }],
        projects: [{ name: "", content: "" }],
        awards: [{ name: "", content: "" }],
        contacts: [{ contact: "", content: "" }]
      }
    };
  },
  components: { ResumeLeftBar, ResumeSearch, ResumePreview },
  methods: {
    preview() {
      this.previewMode = true;
    },
    exitPreview() {
      this.previewMode = false;
    }
  }
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
  #leftBar {
    max-width: 15%;
    float: left;
  }
  #preview {
    float: left;
    width: 50%;
    margin-left: 450px;
    margin-top: 16px;
  }
}

.previewMode > #leftBar {
  display: none;
}
.previewMode #search {
  display: none;
}
.previewMode #preview {
  max-width: 800px;
  margin: 40px 400px;
  background: #ddd;
}
#exitPreview {
  display: none;
  width: 84px;
  height: 35px;
  border-radius: 5px;
  color: #416aa6;
  text-align: center;
  background: none;
  position: relative;
  .icon {
    font-size: 20px;
    fill: #416aa6;
    position: absolute;
    top: 8px;
    left: 0;
  }
}
#exitPreview:hover {
  background: #416aa6;
  color: #fff;
  cursor: pointer;
  svg {
    fill: #fff;
  }
}
.previewMode #exitPreview {
  display: block;
  position: fixed;
  right: 16px;
  bottom: 16px;
}
</style>
