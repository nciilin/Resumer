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
          <h2>个人信息</h2>
          <el-form>
            <el-form-item label="姓名">
              <el-input v-model="profile.name"></el-input>
            </el-form-item>
            <el-form-item label="城市">
              <el-input v-model="profile.city"></el-input>
            </el-form-item>
            <el-form-item label="出生年月">
              <el-input v-model="profile.birth"></el-input>
            </el-form-item>
          </el-form>
        </li>
        <li v-bind:class="{active: currentTab === 1 }">
          <h2>工作经历</h2>
          <el-form>
            <div class="container" v-for="(work, index) in workHistory">
              <el-form-item label="公司">
                <el-input v-model="work.company"></el-input>
              </el-form-item>
              <el-form-item label="内容">
                <el-input v-model="work.content"></el-input>
              </el-form-item>
              <button class="remove" v-on:click="remvoeWorkHistory(index)">
                <svg class="icon" aria-hidden="true">
                  <use xlink:href="#icon-Remove" />
                </svg>
              </button>
              <hr />
            </div>
            <button class="add" v-on:click="addWorkHistory">
              <svg class="icon" aria-hidden="true">
                <use xlink:href="#icon-add" />
              </svg>
            </button>
          </el-form>
        </li>
        <li v-bind:class="{active: currentTab === 2 }">
          <h2>学习经历</h2>
          <el-form>
            <div class="container" v-for="(study, index) in education">
              <el-form-item label="学校">
                <el-input v-model="study.school"></el-input>
              </el-form-item>
              <el-form-item label="内容">
                <el-input v-model="study.content"></el-input>
              </el-form-item>
              <button class="remove" v-on:click="removeStudyHistory(index)">
                <svg class="icon" aria-hidden="true">
                  <use xlink:href="#icon-Remove" />
                </svg>
              </button>
              <hr />
            </div>
            <button class="add" v-on:click="addStudyHistory">
              <svg class="icon" aria-hidden="true">
                <use xlink:href="#icon-add" />
              </svg>
            </button>
          </el-form>
        </li>
        <li v-bind:class="{active: currentTab === 3 }">
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
        </li>
        <li v-bind:class="{active: currentTab === 4 }">
          <h2>获奖经历</h2>
          <el-form>
            <div class="container" v-for="(award, index) in awards">
              <el-form-item label="获奖">
                <el-input v-model="award.name"></el-input>
              </el-form-item>
              <el-form-item label="内容">
                <el-input v-model="award.content"></el-input>
              </el-form-item>
              <button class="remove" v-on:click="removeAwardHistory(index)">
                <svg class="icon" aria-hidden="true">
                  <use xlink:href="#icon-Remove" />
                </svg>
              </button>
              <hr />
            </div>
            <button class="add" v-on:click="addAwardHistory">
              <svg class="icon" aria-hidden="true">
                <use xlink:href="#icon-add" />
              </svg>
            </button>
          </el-form>
        </li>
        <li v-bind:class="{active: currentTab === 5 }">
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
        </li>
      </ol>
    </nav>
  </div>
</template>

<script>
export default {
  name: "ResumeLeftBar",
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
      ],
      profile: {
        name: "",
        city: "",
        birth: ""
      },
      workHistory: [{ company: "", content: "" }],
      education: [{ school: "", content: "" }],
      projects: [{ name: "", content: "" }],
      awards: [{ name: "", content: "" }],
      contacts: [{ contact: "", content: "" }]
    };
  },
  methods: {
    addWorkHistory() {
      this.workHistory.push({
        company: "",
        content: ""
      });
    },
    remvoeWorkHistory(index) {
      this.workHistory.splice(index, 1);
    },
    addStudyHistory() {
      this.education.push({
        school: "",
        content: ""
      });
    },
    removeStudyHistory(index) {
      this.education.splice(index, 1);
    },
    addProjectHistory() {
      this.projects.push({
        name: "",
        content: ""
      });
    },
    removeProjectHistory(index) {
      this.projects.splice(index, 1);
    },
    addAwardHistory() {
      this.awards.push({
        name: "",
        content: ""
      });
    },
    removeAwardHistory(index) {
      this.awards.splice(index, 1);
    },
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