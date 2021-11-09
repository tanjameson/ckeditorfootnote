<template>
    <div id="app">
        <ckeditor @ready="attachInspector" :editor="editor" v-model="editorData" :config="editorConfig"></ckeditor>
    </div>
</template>

<script>

    // ⚠️ NOTE: We don't use @ckeditor/ckeditor5-build-classic any more!
    // Since we're building CKEditor from source, we use the source version of ClassicEditor.
    import ClassicEditor from '@ckeditor/ckeditor5-editor-classic/src/classiceditor';
    import Essentials from '@ckeditor/ckeditor5-essentials/src/essentials';
    import Paragraph from '@ckeditor/ckeditor5-paragraph/src/paragraph';
    import Bold from '@ckeditor/ckeditor5-basic-styles/src/bold';
    import Italic from '@ckeditor/ckeditor5-basic-styles/src/italic';
    import CKeditorInspector from "@ckeditor/ckeditor5-inspector";
    import FootNote from "../plugins/footnote/footnote"
    export default {
        name: 'app',
        methods: {
            attachInspector: editor=> {
                CKeditorInspector.attach(editor);
            }
        },
        data() {
            return {
                editor: ClassicEditor,
                editorData: '<p>Content of the editor.</p>',
                editorConfig: {
                    plugins: [
                  
                        Essentials, Italic,Bold,Paragraph, FootNote
                    ],

                    toolbar: {
                        items: [
                            "bold","italic",'undo','redo', "footnote"
                        ]
                    }
                }
            };
        }
    };
</script>