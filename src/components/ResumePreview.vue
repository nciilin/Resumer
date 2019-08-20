<template>
  <div class="ResumePreview">
    <header class="ContentShow clearfix">
      <p class="ContentTitle">
        Renter Resumer, 8SK4R5
        <span class="ContentAngle">angle</span>
      </p>
    </header>
    <main class="ResumeProfileShow">
      <h1 class="ProfileTitle">{{resume.profile.name || '请填写姓名'}}</h1>
      <p class="ProfileCity">{{resume.profile.city || '请填写城市'}}</p>
      <p class="ProfileBirth">{{resume.profile.birth || '请填写出生年月'}}</p>
      <div class="StickyNotes">
        <ul>
          <li>
            INFORMATION
            <svg class="icon">
              <use xlink:href="#icon-dagou" />
            </svg>
          </li>
          <li>
            COMPANY
            <svg class="icon">
              <use xlink:href="#icon-dagou" />
            </svg>
          </li>
          <li>
            SCHOOL
            <svg class="icon">
              <use xlink:href="#icon-dagou" />
            </svg>
          </li>
          <li>
            PROJECT
            <svg class="icon">
              <use xlink:href="#icon-dagou" />
            </svg>
          </li>
          <li>
            AWARD
            <svg class="icon">
              <use xlink:href="#icon-dagou" />
            </svg>
          </li>
          <li>
            CONTACT
            <svg class="icon">
              <use xlink:href="#icon-dagou" />
            </svg>
          </li>
        </ul>
      </div>
    </main>
    <footer class="ResumeDetail">
      <section v-if="filter(resume.workHistory).length > 0">
        <h2>工作经历</h2>
        <ul>
          <li v-for="work in filter(resume.workHistory)">
            {{work.company}}
            {{work.content}}
          </li>
        </ul>
      </section>
      <section v-if="filter(resume.education).length > 0">
        <h2>学习经历</h2>
        <ul>
          <li v-for="study in filter(resume.education)">
            {{study.school}}
            {{study.degree}}
            {{study.duration}}
          </li>
        </ul>
      </section>
      <section v-if="filter(resume.projects).length > 0">
        <h2>个人项目</h2>
        <ul>
          <li v-for="project in filter(resume.projects)">
            {{project.name}}
            {{project.content}}
          </li>
        </ul>
      </section>
      <section v-if="filter(resume.awards).length > 0">
        <h2>获得奖励</h2>
        <ul>
          <li v-for="award in filter(resume.awards)">
            {{award.name}}
            {{award.content}}
          </li>
        </ul>
      </section>
      <section v-if="filter(resume.contacts).length > 0">
        <h2>联系方式</h2>
        <ul>
          <li v-for="contact in filter(resume.contacts)">
            {{contact.phone}}
            {{contact.email}}
          </li>
        </ul>
      </section>
    </footer>
    <div class="ResumeFooter">
      <p class="Copyright clearfix">
        Copyright@dribbble.com/shots/3035214-Renter-Resume
        <svg class="icon">
          <use xlink:href="#icon-table" />
        </svg>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["resume"],
  methods: {
    filter(array) {
      return array.filter(item => !this.isEmpty(item));
    },
    isEmpty(object) {
      let empty = true;
      for (let key in object) {
        if (object[key]) {
          empty = false;
          break;
        }
      }
      return empty;
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
.ResumePreview {
  width: 800px;
  min-height: 800px;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.25);
  position: relative;
  .ContentShow {
    .ContentTitle {
      float: left;
      width: 800px;
      height: 100px;
      background: #62becb;
      color: #f4f4e9;
      padding: 40px 80px;
      font-size: 21px;
    }
    .ContentAngle {
      float: right;
      font-size: 12px;
    }
  }
  .ResumeProfileShow {
    background: linear-gradient(
      to bottom,
      rgba(224, 223, 225, 1) 0%,
      rgba(229, 229, 229, 1) 100%
    );
    margin-top: 26px;
    padding: 100px 80px;

    .ProfileTitle {
      font-family: inherit;
    }
    .ProfileCity {
      padding-top: 24px;
    }
    .ProfileBirth {
      padding-top: 24px;
    }
    .StickyNotes {
      width: 240px;
      height: 210px;
      background: #0b98a8;
      position: absolute;
      top: 240px;
      right: 32px;
      ul {
        list-style: none;
        padding: 40px 0;
        li {
          text-align: right;
          color: #d6e3e6;
          padding-right: 28px;
          .icon {
            fill: white;
            font-size: 16px;
          }
        }
      }
    }
  }
  .ResumeDetail {
    section {
      background: #dedbde;
      padding: 40px 80px;
      ul {
        list-style: none;
        padding: 20px 0;
      }
    }
  }
  .ResumeFooter {
    width: 100%;
    height: 100px;
    background: #cfcfd1;
    .Copyright {
      padding: 50px;
      font-size: 12px;
      .icon {
        font-size: 18px;
        float: right;
      }
    }
  }
}
</style>