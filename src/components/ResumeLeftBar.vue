<template>
  <div class="wrapper">
    <span class="logo">
      <svg class="icon">
        <use xlink:href="#icon-heart" />
      </svg>
      Resumer
    </span>
    <nav class="clearfix">
      <ul>
        <li
          v-for="i in [0,1,2,3,4,5]"
          v-bind:class="{active: currentTab === i}"
          v-on:click="currentTab = i"
        >
          <svg class="icon">
            <use v-bind:xlink:href="`#icon-${icons[i]}`" />
          </svg>
          {{icons[i]}}
          <span class="triangle"></span>
        </li>
      </ul>
      <ol class="panes">
        <li v-bind:class="{active: currentTab === 0 }">
          <ProfileEditor v-bind:profile="resume.profile" />
        </li>
        <li v-bind:class="{active: currentTab === 1 }">
          <WorkHistoryEditor v-bind:workHistory="resume.workHistory" />
        </li>
        <li v-bind:class="{active: currentTab === 2 }">
          <EducationEditor v-bind:education="resume.education" />
        </li>
        <li v-bind:class="{active: currentTab === 3 }">
          <ProjectEditor v-bind:projects="resume.projects" />
        </li>
        <li v-bind:class="{active: currentTab === 4 }">
          <AwardEditor v-bind:awards="resume.awards" />
        </li>
        <li v-bind:class="{active: currentTab === 5 }">
         <ContactEditor v-bind:contacts="resume.contacts" />
        </li>
      </ol>
    </nav>
  </div>
</template>

<script>
import ProfileEditor from "./ProfileEditor";
import WorkHistoryEditor from "./WorkHistoryEditor";
import EducationEditor from "./EducationEditor";
import ProjectEditor from "./ProjectEditor";
import AwardEditor from "./AwardEditor";
import ContactEditor from './ContactEditor'

export default {
  name: "ResumeLeftBar",
  props: ['resume'],
  components: {
    ProfileEditor,
    WorkHistoryEditor,
    EducationEditor,
    ProjectEditor,
    AwardEditor,
    ContactEditor
  },
  data() {
    return {
      currentTab: 0,
      icons: [
        "information",
        "company",
        "school",
        "project",
        "award",
        "contact"
      ]
    };
  },
  methods: {
  }
};
</script>


<style lang="scss">
.clearfix {
  content: "";
  display: block;
  clear: both;
}
.wrapper {
  box-shadow: 10px 7px 6px 0px rgba(242, 242, 242, 0.84);
  margin-top: 24px;
  .logo {
    font-family: Helvetica;
    font-size: 24px;
    padding: 32px;
  }
  nav {
    margin-top: 72px;
    ul {
      color: #909da3;
      li {
        list-style: none;
        text-align: center;
        padding: 48px 0;
        margin-top: 24px;
        vertical-align: baseline;
        position: relative;
        .icon {
          font-size: 24px;
          position: absolute;
          top: 15px;
          left: 100px;
        }
      }
      .active {
        background: #f6fafd;
        color: #54a19b;
        font-weight: bold;
        .icon {
          fill: #54a19b;
        }
        .triangle {
          width: 0;
          height: 0;
          border-top: 12px solid transparent;
          border-right: 12px solid #1a9285;
          border-bottom: 12px solid #1a9285;
          border-left: 12px solid transparent;
          position: absolute;
          bottom: 0;
          right: 0;
        }
      }
    }
  }
  .panes {
    float: left;
    margin-left: 238px;
    margin-top: -830px;
    width: 420px;
    background: #ffffff;
    overflow: auto;
    box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.25);
    .container {
      position: relative;
      .remove {
        position: absolute;
        top: 0;
        right: 0;
      }
    }
    li {
      list-style: none;
      display: none;
      padding: 32px;
      &.active {
        display: block;
        overflow: auto;
      }
      .add,
      .remove {
        border: none;
        background: none;
        .icon {
          fill: #54a19b;
          width: 24px;
          height: 24px;
        }
      }
      .remove {
        .icon {
          fill: #f56c6c;
        }
      }
      .add:hover,
      .remove:hover {
        cursor: pointer;
        transform: scale(1.4);
      }
    }
  }
}
</style>