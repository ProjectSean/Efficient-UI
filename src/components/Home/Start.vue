<template>
  <article class="markdown-body">
    <h1>开始使用</h1>
    <p>请先<a href="#/home/training">安装</a>本组件库。</p>
    <p>然后在你的代码中写入下面的代码</p>
    <pre><code>import {Button, Tabs, Switch, Dialog} from "arknights-ui";
import from "arknights-ui/dist/lib/arkui.css";</code></pre>
    就可以使用我提供的组件了
    <h2>Vue 单文件组件</h2>
    <p>代码示例：</p>
    <pre>
  <code>  
  &lt;template&gt;
    &lt;div&gt;&lt;Switch&gt;按钮&lt;/Switch&gt;&lt;/div&gt;
  &lt;/template&gt;
  &lt;script&gt;
    import {Button, Tabs, Switch, Dialog} from "arknights-ui";
    import from "arknights-ui/dist/lib/arkui.css";
    export default {
      components: {Switch};
    }
  &lt;/script&gt;
    </code></pre>
  </article>
</template>

<script>
export default {
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
article {
  color: #fff;
  & h1 {
    font-size: 40px;
  }
  & p {
    font-size: 20px;
    & a {
      color: skyblue;
      &:hover {
        text-decoration: none;
      }
    }
  }
  & pre code {
    font-size: 20px;
    color: black;
  }
}
</style>