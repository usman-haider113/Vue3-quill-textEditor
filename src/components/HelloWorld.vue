<template>
  <QuillEditor
    theme="snow"
    v-model:content="getdata"
    content="string"
    content-type="text"
    toolbar="full"
    :modules="modules"
    @update:content="updateContent"
    @focus="handleFocus"
    @blur="handleBlur"
    @text-change="handleTextChange"
    @selection-change="handleSelectionChange"
    @ready="setContentToEditor"
    ref="quillRef"
    style="height:80vh;"
  ></QuillEditor>
</template>
<script>
import BlotFormatter from "quill-blot-formatter/dist/BlotFormatter";
import { QuillEditor } from "@vueup/vue-quill";
import "@vueup/vue-quill/dist/vue-quill.snow.css";
export default {
  components: {
    QuillEditor,
  },
  data() {
    return {
      getdata:'Learning Vue Js',
      modules: {
        name: "blotFormatter",
        module: BlotFormatter,
        options: {},
      },
    };
  },
  methods: {
    handleClick() {
      console.log(
        "html data received from the editor!!!",
        this.$refs.quillRef.getHTML()
      );
    },
    updateContent(content){
      console.log('update content method!!', content)
      alert('update content method gives the content of the editor..!!')

    },
    handleBlur(refElement){
      console.log('Blur event', refElement)
      alert('blur method gives the information about ref attributes....!!!!')
    },
    handleFocus(refElement){
      console.log('on focus ', refElement)
      alert('focus method gives the information about ref attributes if editor gets focused')
    },
    handleTextChange(delta, oldContent, sources){
      console.log('text change method')
      console.log('delta object with all the information', delta)
      console.log('old content', oldContent)
      console.log('sources', sources)
      alert('text change method gets triggered when we try to change data in the editor no matter removal or addition of  new data')
    },
    handleSelectionChange(range, oldRange, sources){
      console.log('selection change method got triggered!!!')
      console.log('delta object with all the information', range)
      console.log('old content', oldRange)
      console.log('sources', sources)
      alert('selection changes gets trigged when we select any of data it gives the range of text that got selected')
    },
    setContentToEditor(quill){
      let content = `<p>Vue quill editor with full toolbar</p>`
      this.$refs.quillRef.setHTML(content)
      console.log('quill object', quill)
      alert('using @ready method we can get, set and perform other functionalities on initialization of editor')
    }
  },
};
</script>
