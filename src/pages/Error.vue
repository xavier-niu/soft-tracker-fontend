<template>
  <Page>
    <div class="page-title">{{pageTitle}}</div>

    <a-icon type="close-circle" class="icon" theme="filled" />
    <div class="title">{{title}}</div>
    <div class="sub-title">{{subTitle}}</div>

    <a-button class="button" @click="backToIndex" type="primary">{{buttonTitle}}</a-button>
  </Page>
</template>

<script>
  import Page from '@/components/Page'

  export default {
    computed: {
      pageTitle() {
        if (!this.$route.query.pageTitle) return ""
        return this.$route.query.pageTitle
      },
      title() {
        if (!this.$route.query.title) return "错误"
        return this.$route.query.title
      },
      subTitle() {
        if (!this.$route.query.subTitle) return "这里好像有点小问题"
        return this.$route.query.subTitle
      },
      buttonTitle() {
        if (!this.$route.query.buttonTitle) return "返回首页"
        return this.$route.query.buttonTitle
      },
      redirectPath() {
        if (!this.$route.query.redirectPath) return "/"
        return this.$route.query.redirectPath
      }
    },
    components: {
      Page
    },
    methods: {
      backToIndex() {
        this.$router.push({path: this.redirectPath})
      }
    }
  }
</script>

<style lang="less">

  @import "../style/common";
  @import "../style/mixin";

  .icon {
    font-size: 70px;
    color: #f31d28;
    display: block;
    margin: 100px auto 0;
  }

  .title {
    .font(24px, @weight: bold);
    line-height: 32px;
    width: 100%;
    text-align: center;
    margin-top: 24px;
  }

  .sub-title {
    width: 15%;
    .font(14px, @size: rgba(0, 0, 0, 0.45));
    .horizontal-center;
    line-height: 22px;
    margin-top: 16px;
    text-align: center;
  }

  .button {
    width: 15%;
    margin-top: 32px;
    .horizontal-center;
  }

</style>
