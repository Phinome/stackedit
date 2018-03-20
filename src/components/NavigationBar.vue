<template>
  <Row type="flex" align="middle" class="docs-material-appbar">
      <Col :span="1" class="docs-logo-wrapper">
        <Icon type="document-text" size="40"></Icon>
      </Col>
      <Col :span="20" class="docs-title">
        <div class="docs-title-outer docs-title-inline-rename" aria-labelledby="docs-title-inner">
          <div class="docs-title-widget goog-inline-block" id="docs-title-widget">
              <div class="docs-title-input-label docs-title-untitled" style="pointer-events: none; max-width: 1539px;">
                  <span class="docs-title-input-label-inner">Untitled document</span>
              </div>
              <input class="docs-title-input" spellcheck="false" type="text" autocomplete="off" guidedhelpid="editor_title" aria-describedby="docs-parent-collections-container-outer"
                  value="Untitled document" tabindex="0" dir="ltr" aria-label="Rename" style="display:none;"
                  data-tooltip="Rename">
          </div>
          <div class="docs-titlebar-badges goog-inline-block">
              <div class="docs-star-container goog-inline-block">
                  <Icon type="ios-star-outline" id="docs-star" style="user-select: none;" aria-checked="false" role="checkbox"
                      aria-hidden="false" aria-disabled="false" data-tooltip="Star" aria-label="Star" tabindex="0"></Icon>
              </div>
              <div class="docs-folder-container goog-inline-block">
                  <div id="docs-folder" class="goog-inline-block goog-control" style="user-select: none;" role="button" aria-hidden="false"
                      data-tooltip="Move to..." aria-label="Move to..." aria-disabled="false" tabindex="0">
                      <div class="docs-icon">
                          <Icon type="ios-folder" class="docs-icon-img-container docs-icon-img docs-icon-folder-solid" aria-hidden="true">&nbsp;</Icon>
                      </div>
                  </div>
              </div>
          </div>
        </div>
        <div class="docs-header-menu">
          <Menu :default-active="activeIndex" class="docs-edit-menu" mode="horizontal">
            <Submenu index="1" class="docs-edit-menu-first">
              <template slot="title">文件</template>
              <MenuItem index="2-1">选项1</MenuItem>
              <MenuItem index="2-2">选项2</MenuItem>
              <MenuItem index="2-3">选项3</MenuItem>
            </Submenu>
            <Submenu index="2" >
              <template slot="title">编辑</template>
              <MenuItem index="2-1">选项1</MenuItem>
              <MenuItem index="2-2">选项2</MenuItem>
              <MenuItem index="2-3">选项3</MenuItem>
            </Submenu>
            <Submenu index="3" >
                <template slot="title">视图</template>
                <MenuItem index="2-1">选项1</MenuItem>
                <MenuItem index="2-2">选项2</MenuItem>
                <MenuItem index="2-3">选项3</MenuItem>
            </Submenu>
            <Submenu index="4" >
                <template slot="title">插入</template>
                <MenuItem index="2-1">选项1</MenuItem>
                <MenuItem index="2-2">选项2</MenuItem>
                <MenuItem index="2-3">选项3</MenuItem>
            </Submenu>
            <Submenu index="5" >
                <template slot="title">工具</template>
                <MenuItem index="2-1">选项1</MenuItem>
                <MenuItem index="2-2">选项2</MenuItem>
                <MenuItem index="2-3">选项3</MenuItem>
            </Submenu>
            <Submenu index="6" >
                <template slot="title">帮助</template>
                <MenuItem index="2-1">选项1</MenuItem>
                <MenuItem index="2-2">选项2</MenuItem>
                <MenuItem index="2-3">选项3</MenuItem>
            </Submenu>
          </Menu>
        </div>
      </Col>
      <Col :span="3">col-3</Col>
  </Row>
</template>

<script>
import {mapState, mapMutations, mapGetters, mapActions} from 'vuex';
import {Row, Col, Menu, MenuItem, Submenu} from 'element-ui';
import editorSvc from '../services/editorSvc';
import syncSvc from '../services/syncSvc';
import publishSvc from '../services/publishSvc';
import animationSvc from '../services/animationSvc';
import utils from '../services/utils';

export default {
    components: {
        Row,
        Col,
        Menu,
        MenuItem,
        Submenu,
    },
    data: () => ({
        activeIndex: '1',
        mounted: false,
        title: '',
        titleFocus: false,
        titleHover: false,
    }),
    computed: {
        ...mapState(['offline']),
        ...mapState('queue', ['isSyncRequested', 'isPublishRequested', 'currentLocation']),
        ...mapState('layout', ['canUndo', 'canRedo']),
        ...mapState('content', ['revisionContent']),
        ...mapGetters('layout', ['styles']),
        ...mapGetters('syncLocation', {
            syncLocations: 'current',
        }),
        ...mapGetters('publishLocation', {
            publishLocations: 'current',
        }),
        isSyncPossible() {
            return this.$store.getters['workspace/syncToken'] || this.$store.getters['syncLocation/current'].length;
        },
        showSpinner() {
            return !this.$store.state.queue.isEmpty;
        },
        titleWidth() {
            if (!this.mounted) {
                return 0;
            }
            this.titleFakeElt.textContent = this.title;
            const width = this.titleFakeElt.getBoundingClientRect().width + 2; // 2px for the caret
            return width < this.styles.titleMaxWidth ? width : this.styles.titleMaxWidth;
        },
        titleScrolling() {
            const result = this.titleHover && !this.titleFocus;
            if (this.titleInputElt) {
                if (result) {
                    const scrollLeft = this.titleInputElt.scrollWidth - this.titleInputElt.offsetWidth;
                    animationSvc
                        .animate(this.titleInputElt)
                        .scrollLeft(scrollLeft)
                        .duration(scrollLeft * 10)
                        .easing('inOut')
                        .start();
                } else {
                    animationSvc
                        .animate(this.titleInputElt)
                        .scrollLeft(0)
                        .start();
                }
            }
            return result;
        },
    },
    methods: {
        ...mapMutations('content', ['setRevisionContent']),
        ...mapActions('content', ['restoreRevision']),
        ...mapActions('data', ['toggleExplorer', 'toggleSideBar']),
        undo() {
            return editorSvc.clEditor.undoMgr.undo();
        },
        redo() {
            return editorSvc.clEditor.undoMgr.redo();
        },
        requestSync() {
            if (this.isSyncPossible && !this.isSyncRequested) {
                syncSvc.requestSync();
            }
        },
        requestPublish() {
            if (this.publishLocations.length && !this.isPublishRequested) {
                publishSvc.requestPublish();
            }
        },
        pagedownClick(name) {
            if (this.$store.getters['content/isCurrentEditable']) {
                editorSvc.pagedownEditor.uiManager.doClick(name);
            }
        },
        editTitle(toggle) {
            this.titleFocus = toggle;
            if (toggle) {
                this.titleInputElt.setSelectionRange(0, this.titleInputElt.value.length);
            } else {
                const title = this.title.trim();
                if (title) {
                    this.$store.dispatch('file/patchCurrent', {name: utils.sanitizeName(title)});
                } else {
                    this.title = this.$store.getters['file/current'].name;
                }
            }
        },
        submitTitle(reset) {
            if (reset) {
                this.title = '';
            }
            this.titleInputElt.blur();
        },
    },
    created() {
        this.$store.watch(
            () => this.$store.getters['file/current'].name,
            name => {
                this.title = name;
            },
            {immediate: true},
        );
    },
    mounted() {
        this.titleFakeElt = this.$el.querySelector('.navigation-bar__title--fake');
        this.titleInputElt = this.$el.querySelector('.navigation-bar__title--input');
        this.mounted = true;
    },
};
</script>

<style lang="scss">
@import 'common/variables.scss';

.docs-material-appbar {
    height: 68px;
    margin: 0;
    padding: 0 16px;

    .el-menu--horizontal {
        border-bottom: none;
    }
    .el-menu-item {
        height: auto;
        padding: 3px 7px 5px 7px;
        font-size: 14px;
        line-height: initial;
    }
    .el-menu--horizontal > .el-submenu .el-submenu__title {
        height: auto;
        line-height: initial;
    }

    .docs-edit-menu-first {
        .el-submenu__title {
            padding: 0 8px;
        }
    }

    .docs-logo-wrapper {
        margin: 4px 0 4px 8px;
        padding: 8px;
        border-radius: 50%;
    }

    .docs-title {
        padding-top: 9px;
        font-size: 18px;
        align-self: flex-start;
    }

    .docs-title-outer {
        display: flex;
        align-items: center;
        line-height: 29px;
    }

    .docs-title-widget {
        position: relative;
    }

    .docs-title-input-label {
        margin: 0;
        padding: 2px 8px;
        font: 18px Arial;
        font-style: italic;
        color: #777;
        line-height: 22px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: pre;
        z-index: 1;
    }
    .docs-title-input {
        position: absolute;
        top: 0;
        left: 0;
    }

    .docs-titlebar-badges {
        display: flex;
        align-items: center;
        justify-content: space-between;

        .docs-star-container,
        .docs-folder-container {
            width: 29px;
            height: 29px;
            text-align: center;
        }
    }
}

$r: 10px;
$d: $r * 2;
$b: $d/10;
$t: 3000ms;

.navigation-bar__spinner {
    width: 24px;
    margin: 7px 0 0 8px;

    .icon {
        width: 24px;
        height: 24px;
        color: transparentize($error-color, 0.5);
    }
}

.spinner {
    width: $d;
    height: $d;
    display: block;
    position: relative;
    border: $b solid transparentize($navbar-color, 0.5);
    border-radius: 50%;
    margin: 2px;

    &::before,
    &::after {
        content: '';
        position: absolute;
        display: block;
        width: $b;
        background-color: $navbar-color;
        border-radius: $b * 0.5;
        transform-origin: 50% 0;
    }

    &::before {
        height: $r * 0.4;
        left: $r - $b * 1.5;
        top: 50%;
        animation: spin $t linear infinite;
    }

    &::after {
        height: $r * 0.6;
        left: $r - $b * 1.5;
        top: 50%;
        animation: spin $t/4 linear infinite;
    }
}

@keyframes spin {
    to {
        transform: rotate(360deg);
    }
}

@keyframes blink {
    50% {
        opacity: 1;
    }
}
</style>
