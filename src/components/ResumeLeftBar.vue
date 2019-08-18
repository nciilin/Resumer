<template>
  <div class="wrapper">
    <span class="logo">
      <svg class="icon">
        <use xlink:href="#icon-heart" />
      </svg>
      Resumer
    </span>
    <nav>
      <ul>
        <li>
          <svg class="icon">
            <use xlink:href="#icon-information" />
          </svg>Information
        </li>

        <li>
          <svg class="icon">
            <use xlink:href="#icon-company" />
          </svg>Company
        </li>

        <li>
          <svg class="icon">
            <use xlink:href="#icon-school" />
          </svg>School
        </li>

        <li>
          <svg class="icon">
            <use xlink:href="#icon-project-copy" />
          </svg>Project
        </li>

        <li>
          <svg class="icon">
            <use xlink:href="#icon-award" />
          </svg>Award
        </li>

        <li>
          <svg class="icon">
            <use xlink:href="#icon-contact" />
          </svg>Contact
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  name: "ResumeLeftBar"
};
</script>

<style lang="scss">
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
        padding: 40px 0;
        margin-top: 24px;
        vertical-align: baseline;
        position: relative;
        svg {
          font-size: 24px;
          position: absolute;
          top: 0;
          left: 100px;
        }
      }
    }
  }
}
</style>