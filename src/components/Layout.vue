<template>
  <div class="layout" :class="{'layout--revision': revisionContent}">
    <navigation-bar></navigation-bar>
    <div class="docs-toolbar-wrapper"></div>
  </div>
</template>

<script>
import {mapState, mapGetters, mapActions} from 'vuex';
import NavigationBar from './NavigationBar';
import ButtonBar from './ButtonBar';
import StatusBar from './StatusBar';
import Explorer from './Explorer';
import SideBar from './SideBar';
import Editor from './Editor';
import Preview from './Preview';
import Tour from './Tour';
import StickyComment from './gutters/StickyComment';
import CurrentDiscussion from './gutters/CurrentDiscussion';
import FindReplace from './FindReplace';
import editorSvc from '../services/editorSvc';

export default {
    components: {
        NavigationBar,
        ButtonBar,
        StatusBar,
        Explorer,
        SideBar,
        Editor,
        Preview,
        Tour,
        StickyComment,
        CurrentDiscussion,
        FindReplace,
    },
    computed: {
        ...mapState('content', ['revisionContent']),
        ...mapState('discussion', ['stickyComment']),
        ...mapGetters('layout', ['constants', 'styles']),
        ...mapGetters('data', ['layoutSettings']),
        showFindReplace() {
            return !!this.$store.state.findReplace.type;
        },
    },
    methods: {
        ...mapActions('layout', ['updateBodySize']),
        saveSelection: () => editorSvc.saveSelection(true),
    },
    created() {
        this.updateBodySize();
        window.addEventListener('resize', this.updateBodySize);
        window.addEventListener('keyup', this.saveSelection);
        window.addEventListener('mouseup', this.saveSelection);
        window.addEventListener('focusin', this.saveSelection);
        window.addEventListener('contextmenu', this.saveSelection);
    },
    mounted() {
        const editorElt = this.$el.querySelector('.editor__inner');
        const previewElt = this.$el.querySelector('.preview__inner-2');
        const tocElt = this.$el.querySelector('.toc__inner');
        editorSvc.init(editorElt, previewElt, tocElt);

        // Focus on the editor every time reader mode is disabled
        this.$watch(() => this.styles.showEditor, showEditor => showEditor && editorSvc.clEditor.focus());
    },
    destroyed() {
        window.removeEventListener('resize', this.updateStyle);
        window.removeEventListener('keyup', this.saveSelection);
        window.removeEventListener('mouseup', this.saveSelection);
        window.removeEventListener('focusin', this.saveSelection);
        window.removeEventListener('contextmenu', this.saveSelection);
    },
};
</script>

<style lang="scss">
@import 'common/variables.scss';

.layout {
    position: absolute;
    width: 100%;
    height: 100%;

    .docs-toolbar-wrapper {
        min-height: 35px;
        padding: 0 21px 0 22px;
        border-top: 1px solid #e0e0e0;
        border-bottom: 1px solid #e0e0e0;
        background: #fff;
    }
}

.layout__panel {
    position: relative;
    width: 100%;
    height: 100%;
    flex: none;
    overflow: hidden;
}

.layout__panel--navigation-bar {
    background-color: $navbar-bg;
}

.layout__panel--status-bar {
    background-color: #007acc;
}

.layout__panel--editor {
    background-color: $editor-background-light;

    .app--dark & {
        background-color: $editor-background-dark;
    }

    .gutter__background,
    .comment-list__current-discussion,
    .sticky-comment,
    .current-discussion {
        background-color: mix(#000, $editor-background-light, 6.7%);
        border-color: $editor-background-light;

        .app--dark & {
            background-color: mix(#fff, $editor-background-dark, 6.7%);
            border-color: $editor-background-dark;
        }
    }
}

$preview-background-light: #f3f3f3;
$preview-background-dark: #252525;

.layout__panel--preview,
.layout__panel--button-bar {
    background-color: $preview-background-light;

    .app--dark & {
        background-color: $preview-background-dark;
    }
}

.layout__panel--preview {
    .gutter__background,
    .comment-list__current-discussion,
    .sticky-comment,
    .current-discussion {
        background-color: mix(#000, $preview-background-light, 6.7%);
        border-color: $preview-background-light;
    }
}

.layout__panel--explorer,
.layout__panel--side-bar {
    background-color: #dadada;
}

.layout__panel--find-replace {
    background-color: #e6e6e6;
    position: absolute;
    left: 0;
    bottom: 0;
    width: 300px;
    height: auto;
    border-top-right-radius: $border-radius-base;
}
</style>
