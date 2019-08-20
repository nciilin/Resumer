<template>
  <div class="ResumePreview">
    <h1>{{resume.profile.name || '请填写姓名'}}</h1>
    <p>{{resume.profile.city || '请填写城市'}} | {{resume.profile.birth || '请填写出生年月'}}</p>
    <hr />
    <section v-if="filter(resume.projects).length > 0">
      <h2>项目</h2>
      <ul>
        <li v-for="project in filter(resume.projects)">
          {{project.name}}
          {{project.content}}
        </li>
      </ul>
    </section>
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
      <h2>项目经历</h2>
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
          {{contact.name}}
          {{contact.content}}
        </li>
      </ul>
    </section>
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
.ResumePreview {
  background: #ffffff;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.25);
  section {
    ul {
      list-style: none;
    }
  }
}
</style>