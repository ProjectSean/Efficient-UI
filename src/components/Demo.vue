<template>
  <div class="demo">
    <h2>{{ title }}</h2>
    <div class="demo-component">
      <component :is="component" />
    </div>
    <div
      v-if="!codeVisible"
      class="demo-actions"
      @click="codeVisible = !codeVisible"
    >
      显示代码
    </div>
    <div v-else class="demo-actions" @click="codeVisible = !codeVisible">
      隐藏代码
    </div>
    <div class="demo-code" v-if="codeVisible">
      <pre class="language-html" v-html="html" />
      <p>*请将引入路径修改成您自己指定的路径</p>
    </div>
  </div>
</template>

<script lang="ts">
import { computed, ref } from "vue";
import "prismjs";
const Prism = (window as any).Prism;
export default {
  props: {
    title: String,
    component: Object,
  },
  setup(props) {
    const html = computed(() => {
      return Prism.highlight(
        props.component.__sourceCode,
        Prism.languages.html,
        "html"
      );
    });
    const codeVisible = ref(false);
    return { Prism, html, codeVisible };
  },
};
</script>

<style lang="scss" scoped>
$border-color: #d9d9d9;
h1 {
  color: #fff;
}
.demo {
  border: 1px solid $border-color;
  margin: 16px 0 32px;
  min-width: 300px;
  > h2 {
    font-size: 20px;
    padding: 8px 16px;
    border-bottom: 1px solid $border-color;
    color: #fff;
  }
  &-component {
    padding: 16px;
  }
  &-actions {
    padding: 8px 16px;
    border-top: 1px dashed $border-color;
    color: #fff;
    cursor: pointer;
    text-align: center;
  }
  &-code {
    padding: 8px 16px;
    border-top: 1px dashed $border-color;
    > pre {
      line-height: 1.1;
      font-family: Consolas, "Courier New", Courier, monospace;
      margin: 0;
      color: #fff;
    }
    > p {
      margin-top: 5px;
      font-style: italic;
      font-size: 14px;
      color: #fff;
    }
  }
}
</style>