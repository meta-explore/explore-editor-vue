<template>
  <div id="explore-editor-vue"></div>
</template>
<script>
import ExploreEditor from "explore-editor";
import plugins from "explore-editor/lib/plugins";
import "explore-editor/lib/assets/css/editor.css";
import "explore-editor/lib/assets/css/editor-contents.css";
export default {
  name: 'ExploreEditor',
  props: {
    lang: String,
  },
  methods: {
    getLanguage(lang) {
      switch (typeof lang) {
          case 'object':
            return lang;
          case 'string':
            switch (lang) {
              case 'en':
                return require('explore-editor/lib/lang/en');
              case 'da':
                return require('explore-editor/lib/lang/da');
              case 'de':
                return require('explore-editor/lib/lang/de');
              case 'es':
                return require('explore-editor/lib/lang/es');
              case 'fr':
                return require('explore-editor/lib/lang/fr');
              case 'ja':
                return require('explore-editor/lib/lang/ja');
              case 'ko':
                return require('explore-editor/lib/lang/ko');
              case 'pt_br':
                return require('explore-editor/lib/lang/pt_br');
              case 'ru':
                return require('explore-editor/lib/lang/ru');
              case 'zh_cn':
                return require('explore-editor/lib/lang/zh_cn');
              default:
                return require('explore-editor/lib/lang/en');
            }
          default:
        }
        return require('explore-editor/lib/lang/en');
    }
  },
  mounted() {
    const editorId = document.getElementById("explore-editor-vue");
    ExploreEditor.create(editorId, {
      lang: this.getLanguage(this.lang),
      plugins: plugins,
    });
  }
}
</script>