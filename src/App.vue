<template>
  <a-form :form="form" @submit="handleSubmit">
    <a-form-item label="note">
      <a-input
        v-decorator="[
          'note',
          {
            rules: [
              { required: true, message: 'Please input your note!' },
              {
                max: 10,
                message: 'Please enter a note with a maximum length of 10',
              },
              {
                validator,
              },
            ],
          },
        ]"
      />
    </a-form-item>
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
    this.form = this.$form.createForm(this);
  },
  methods: {
    validator(rule, value, callback) {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          if (String(value).startsWith("A")) {
            callback();
            resolve();
          } else {
            callback("自定义校验：请使用字母A作为开头");
            reject("自定义校验：请使用字母A作为开头");
          }
        }, 100);
      });
    },
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields();
    },
  },
};
</script>

<style>
form {
  border: 1px dotted red;
  margin: 2rem !important;
  padding: 1rem !important;
}
</style>
