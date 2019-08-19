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
        <li v-for="i in [0,1,2,3,4,5]"
         v-bind:class="{active: currentTab === i}">tab{{i + 1}}</li>
       
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
      icons: ["information", "company", "school", "project", "award", "contact"]
    };
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
    height: 400px;
    background: #ffffff;
    box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.25);
    li {
      list-style: none;
      display: none;
      &.active {
        display: block;
      }
    }
  }
}
</style>