<template>
  <a-form :form="form" @submit="handleSubmit">
    <a-form-item :wrapper-col="{ span: 12, offset: 5 }">
      <a-button type="primary" html-type="submit"> Submit </a-button>
    </a-form-item>
  </a-form>
</template>

<script>
export default {
  name: "App",
  data: () => {
    return {};
  },
  beforeCreate() {
    // 初始化表单实例，绑定 自定义 onChange 事件
    this.form = this.$form.createForm(this, {
      onValuesChange: () => {}
    });
  },
  methods: {}
};
</script>

<style>
form {
  border: 1px dotted red;
  margin: 2rem !important;
  padding: 1rem !important;
}
</style>
