<template>
  <div class="docs-material-appbar">
    <div>
        <div class="docs-header-container">
            <div class="docs-title-container">
                <div id="docs-branding-container" class="docs-branding-documents docs-branding-crossfade-transition-disabled">
                    <a href="https://docs.google.com/document/?authuser=0&amp;usp=docs_web" data-tooltip="Docs home" aria-label="Docs home">
                        <div id="docs-branding-logo">
                            <iconFileImage id="docs-branding-icon" />
                        </div>
                    </a>
                </div>
                <div id="docs-titlebar">
                  <div id="docs-titlebar">
                      <div class="docs-title-outer docs-title-inline-rename" aria-labelledby="docs-title-inner">
                          <div class="docs-title-widget goog-inline-block" id="docs-title-widget">
                              <div class="docs-title-input-label docs-title-untitled" style="pointer-events: none; max-width: 1539px;">
                                  <span class="docs-title-input-label-inner">Untitled document</span>
                              </div>
                              <input class="docs-title-input" spellcheck="false" type="text" autocomplete="off" guidedhelpid="editor_title" aria-describedby="docs-parent-collections-container-outer" value="Untitled document" tabindex="0" dir="ltr" aria-label="Rename" style="visibility: visible; width: 150px;" data-tooltip="Rename">
                          </div>
                          <div class="docs-parent-collections-container-outer goog-inline-block goog-control" id="docs-parent-collections-container-outer" style="display: none; user-select: none;" aria-hidden="true" aria-disabled="false"></div>
                          <div class="docs-titlebar-badges goog-inline-block">
                              <div class="docs-templates-badge-container goog-inline-block"></div>
                              <div class="docs-dlp-container goog-inline-block"></div>
                              <div class="docs-star-container goog-inline-block">
                                  <div id="docs-star" class="goog-inline-block jfk-star" style="user-select: none;" aria-checked="false" role="checkbox" aria-hidden="false" aria-disabled="false" data-tooltip="Star" aria-label="Star" tabindex="0"></div>
                              </div>
                              <div class="docs-folder-container goog-inline-block">
                                  <div id="docs-folder" class="goog-inline-block goog-control" style="user-select: none;" role="button" aria-hidden="false" data-tooltip="Move to..." aria-label="Move to..." aria-disabled="false" tabindex="0">
                                      <div class="docs-icon goog-inline-block ">
                                          <div class="docs-icon-img-container docs-icon-img docs-icon-folder-solid" aria-hidden="true">&nbsp;</div>
                                      </div>
                                  </div>
                              </div>
                              <div class="docs-activity-indicator-container goog-inline-block">
                                  <div id="docs-activity-indicator" class="goog-inline-block" aria-live="polite" data-tooltip="" aria-label="You are online">
                                      <div class="jfk-activityIndicator jfk-activityIndicator-small">
                                          <div>
                                              <div class="jfk-activityIndicator-circle-transition">
                                                  <div class="jfk-activityIndicator-mask" style="left: 8px; top: 0px; width: 8px; height: 16px;">
                                                      <div class="jfk-activityIndicator-circle" style="background-color: rgb(255, 255, 255); left: -8px; top: 0px;"></div>
                                                      <div class="jfk-activityIndicator-circle jfk-activityIndicator-transition" style="background-color: rgb(119, 119, 119); left: 0px; top: 0px; width: 0px;"></div>
                                                  </div>
                                                  <div class="jfk-activityIndicator-mask" style="left: 0px; top: 0px; width: 8px; height: 16px;">
                                                      <div class="jfk-activityIndicator-circle" style="background-color: rgb(153, 153, 153); display: none;"></div>
                                                      <div class="jfk-activityIndicator-circle jfk-activityIndicator-transition-second" style="background-color: rgb(255, 255, 255); width: 16px; left: 0px;"></div>
                                                  </div>
                                              </div>
                                          </div>
                                          <div class="jfk-activityIndicator-icon" style="opacity: 0;"></div>
                                      </div>
                                  </div>
                              </div>
                          </div>
                      </div>
                  </div>
                    <!-- <div class="docs-titlebar-buttons docs-material">
                            <div id="docs-presence-container" class="goog-inline-block docs-titlebar-button">
                                <div id="docs-presence" class="goog-inline-block">
                                    <div class="docs-presence-plus-widget goog-inline-block" style="width: 0px;">
                                        <div class="docs-presence-plus-widget-inner goog-inline-block">
                                            <div id=":mw.presenceStatusContent" class="docs-presence-plus-widget-status"></div>
                                            <div class="docs-presence-plus-widget-collabs goog-inline-block" aria-described-by=":mw.presenceStatusContent"></div>
                                        </div>
                                    </div>
                                </div>
                                <div class="goog-inline-block" style="display: none;">
                                    <div role="button" id="docs-chat" class="goog-inline-block jfk-button jfk-button-standard jfk-button-narrow docs-chat" aria-disabled="false" aria-label="Show chat" tabindex="0" data-tooltip="Show chat" style="user-select: none;">
                                        <div class="docs-icon goog-inline-block ">
                                            <div class="docs-icon-img-container docs-icon-img docs-icon-chat-person-wide-grey900" aria-hidden="true">&nbsp;</div>
                                        </div>
                                        <div class="docs-chat-badge"></div>
                                    </div>
                                </div>
                            </div>
                            <div class="goog-inline-block">
                                <div role="button" id="docs-docos-commentsbutton" class="goog-inline-block jfk-button jfk-button-standard docs-titlebar-button jfk-button-clear-outline" aria-disabled="false" aria-pressed="false" data-tooltip="Open comments thread (⌘+Option+Shift+A)" aria-label="Open comments thread (⌘+Option+Shift+A)" value="undefined" style="user-select: none;" aria-hidden="false" tabindex="0">
                                    <div class="docs-icon goog-inline-block">
                                        <div class="docs-icon-img-container docs-icon-img docs-icon-insert-comment-24" aria-hidden="true">&nbsp;</div>
                                    </div>
                                </div>
                                <div id="docs-docos-caret" style="display: none;" class="docos-enable-new-header">
                                    <div class="docs-docos-caret-outer"></div>
                                    <div class="docs-docos-caret-inner"></div>
                                </div>
                            </div>
                            <span displayname="null" vsjson="{&quot;role&quot;:0,&quot;summary&quot;:&quot;Private to only me&quot;,&quot;details&quot;:&quot;&quot;,&quot;visibilityState&quot;:&quot;private&quot;,&quot;restrictedToDomain&quot;:true,&quot;restrictedToSingleUserScope&quot;:true,&quot;hasInvalidEntries&quot;:false,&quot;hasNamedPartiesForPublish&quot;:false,&quot;publishVisibilityState&quot;:&quot;named_parties&quot;}" id="docs-titlebar-share-client-button" class="scb-container">
                                <div role="button" class="goog-inline-block jfk-button jfk-button-action docs-titlebar-button" aria-disabled="false" aria-label="Share. Private to only me. " style="user-select: none;" tabindex="0">
                                    <span class="scb-icon apps-share-sprite scb-button-icon  scb-private-icon-white">&nbsp;</span>Share</div>
                            </span>
                            <div class="onegoogle-material-minibar">
                                <div class="gb_Xa gb_8d gb_tb gb_Za" id="gb">
                                    <div class="gb_Cc gb_nb gb_Bc gb_4d" ng-non-bindable="" style="padding:0;height:auto;display:block">
                                        <div class="gb_Dc gb_7d" style="display:block">
                                            <div class="gb_5d"></div>
                                            <div class="gb_kb gb_8c gb_Kg gb_R gb_Af gb_rb">
                                                <div class="gb_Pc gb_mb gb_Kg gb_R">
                                                    <a class="gb_b gb_ib gb_R" href="" role="button" tabindex="0" aria-expanded="false">
                                                        <span class="gb_db gbii"></span>
                                                    </a>
                                                    <div class="gb_vb"></div>
                                                    <div class="gb_ub"></div>
                                                </div>
                                                <div class="gb_wb gb_fa" aria-label="Account Information" aria-hidden="true" img-loaded="1">
                                                    <div class="gb_zb">
                                                        <a class="gb_Ab gb_Xf gb_Cb" aria-label="Change profile picture." href="https://plus.google.com/u/0/me" target="_blank">
                                                            <div class="gb_Db gbip" title="Profile"></div>
                                                            <span class="gb_ob">Change</span>
                                                        </a>
                                                        <div class="gb_Bb">
                                                            <div class="gb_Eb gb_Fb">long phinome</div>
                                                            <div class="gb_Hb">long.phinome@gmail.com</div>
                                                            <div class="gb_yb">
                                                                <a href="https://plus.google.com/u/0/me" target="_blank">Google+ Profile</a>–
                                                                <a href="https://myaccount.google.com/privacypolicy" target="_blank">Privacy</a>
                                                            </div>
                                                            <a class="gb_Ea gb_Uf gbp1 gb_Ke gb_Ib" href="https://myaccount.google.com/?utm_source=OGB&amp;utm_medium=act" target="_blank">My Account</a>
                                                        </div>
                                                    </div>
                                                    <div class="gb_Nb">
                                                        <div class="gb_Pb gb_bb" aria-hidden="true">
                                                            <a class="gb_Rb gb_Zb" href="/document/d/1jBjsxejvxDI3a0v6yBw6XMqJKNdLd810RDka0dZyRsw/edit?authuser=0" target="_blank" rel="noreferrer">
                                                                <img class="gb_1b gb_Cb" src="https://lh3.googleusercontent.com/-sNG-LASLFUc/AAAAAAAAAAI/AAAAAAAAAAA/AGi4gfyUubhMLuouKeQ-i2Cyb0DHcuxtuQ/s48-c-mo/photo.jpg" alt="Profile">
                                                                <div class="gb_Tb">
                                                                    <div class="gb_2b">long phinome</div>
                                                                    <div class="gb_3b" dir="ltr">long.phinome@gmail.com (default)</div>
                                                                </div>
                                                            </a>
                                                        </div>
                                                        <a class="gb_5b gb_bb" href="https://myaccount.google.com/brandaccounts?authuser=0&amp;continue=https://docs.google.com/document/d/1jBjsxejvxDI3a0v6yBw6XMqJKNdLd810RDka0dZyRsw/edit&amp;service=/document/d/1jBjsxejvxDI3a0v6yBw6XMqJKNdLd810RDka0dZyRsw/edit%3Fauthuser%3D%24authuser" aria-hidden="true">
                                                            <span class="gb_6b gb_gc"></span>
                                                            <div class="gb_7b">All your Brand Accounts »</div>
                                                        </a>
                                                    </div>
                                                    <div class="gb_pb gb_bb">
                                                        <div class="gb_qb"></div>
                                                    </div>
                                                    <div class="gb_Jb">
                                                        <div>
                                                            <a class="gb_Ea gb_Tf gb_Ke gb_Ib" href="https://accounts.google.com/AddSession?service=wise&amp;continue=https://docs.google.com/document/d/1jBjsxejvxDI3a0v6yBw6XMqJKNdLd810RDka0dZyRsw/edit" target="_blank">Add account</a>
                                                        </div>
                                                        <div>
                                                            <a class="gb_Ea gb_Vf gb_3f gb_Ke gb_Ib" id="gb_71" href="https://accounts.google.com/Logout?service=wise&amp;continue=https://docs.google.com" target="_top">Sign out</a>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <div class="docs-docos-activitybox docos-enable-new-header" role="dialog" aria-label="Comment stream box." tabindex="0" style="visibility: hidden; display: none;">
                                <div class="docs-docos-activitybox-inner" dir="ltr" style="text-align: left;">
                                    <div class="docos docos-streampane-container docos-enable-docs-header" tabindex="0">
                                        <div class="docos-streampane-content">
                                            <div class="docos-streampane-header">
                                                <div class="docos-new-comment-button docs-material jfk-button jfk-button-standard" role="button" data-tooltip="Add a comment" aria-label="Add a comment" aria-disabled="false" style="user-select: none;" tabindex="0">
                                                    <div class="docos-icon goog-inline-block docos-new-comment-icon docos-icon-add-comment-size">
                                                        <div class="docos-icon-img docos-icon-img-container docos-icon-add-comment docos-icon-img-hdpi" aria-hidden="true"></div>
                                                    </div>Comment</div>
                                                <div class="docos-notification-settings">
                                                    <div class="goog-inline-block goog-flat-menu-button" role="button" aria-expanded="false" aria-haspopup="true" data-tooltip="Change email notification settings for this document." aria-label="Change email notification settings for this document." style="user-select: none;" aria-disabled="false" tabindex="0">
                                                        <div class="goog-inline-block goog-flat-menu-button-caption">
                                                            <div class="docos-ns-caption">
                                                                <div class="docos-icon goog-inline-block docos-ns-caption-icon docos-icon-bell-size">
                                                                    <div class="docos-icon-img docos-icon-img-container docos-icon-bell" aria-hidden="true"></div>
                                                                </div>
                                                                <div class="docos-ns-caption-text">
                                                                    <div class="docos-ns-caption-text-value">Notifications</div>
                                                                </div>
                                                            </div>
                                                        </div>
                                                        <div class="goog-inline-block goog-flat-menu-button-dropdown" aria-hidden="true">&nbsp;</div>
                                                    </div>
                                                </div>
                                            </div>
                                            <div class="docos-streampane-readonlytext show-on-readonly goog-inline-block">You do not have permission to add comments.</div>
                                            <div class="docos docos-stream-view"></div>
                                        </div>
                                        <div></div>
                                    </div>
                                    <div tabindex="0" style="position: absolute;"></div>
                                </div>
                            </div>
                        </div> -->
                </div>
            </div>
            <div class="docs-headerbar-container"></div>
        </div>
    </div>
    <div class="B"></div>
    <div class="C"></div>
</div>
</template>

<script>
import { mapState, mapMutations, mapGetters, mapActions } from 'vuex';
import editorSvc from '../services/editorSvc';
import syncSvc from '../services/syncSvc';
import publishSvc from '../services/publishSvc';
import animationSvc from '../services/animationSvc';
import utils from '../services/utils';

export default {
  data: () => ({
    mounted: false,
    title: '',
    titleFocus: false,
    titleHover: false,
  }),
  computed: {
    ...mapState([
      'offline',
    ]),
    ...mapState('queue', [
      'isSyncRequested',
      'isPublishRequested',
      'currentLocation',
    ]),
    ...mapState('layout', [
      'canUndo',
      'canRedo',
    ]),
    ...mapState('content', [
      'revisionContent',
    ]),
    ...mapGetters('layout', [
      'styles',
    ]),
    ...mapGetters('syncLocation', {
      syncLocations: 'current',
    }),
    ...mapGetters('publishLocation', {
      publishLocations: 'current',
    }),
    isSyncPossible() {
      return this.$store.getters['workspace/syncToken'] ||
        this.$store.getters['syncLocation/current'].length;
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
      return width < this.styles.titleMaxWidth
        ? width
        : this.styles.titleMaxWidth;
    },
    titleScrolling() {
      const result = this.titleHover && !this.titleFocus;
      if (this.titleInputElt) {
        if (result) {
          const scrollLeft = this.titleInputElt.scrollWidth - this.titleInputElt.offsetWidth;
          animationSvc.animate(this.titleInputElt)
            .scrollLeft(scrollLeft)
            .duration(scrollLeft * 10)
            .easing('inOut')
            .start();
        } else {
          animationSvc.animate(this.titleInputElt)
            .scrollLeft(0)
            .start();
        }
      }
      return result;
    },
  },
  methods: {
    ...mapMutations('content', [
      'setRevisionContent',
    ]),
    ...mapActions('content', [
      'restoreRevision',
    ]),
    ...mapActions('data', [
      'toggleExplorer',
      'toggleSideBar',
    ]),
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
          this.$store.dispatch('file/patchCurrent', { name: utils.sanitizeName(title) });
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
      (name) => {
        this.title = name;
      }, { immediate: true });
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
  .docs-header-container,
  .docs-title-container {
    display: flex;
  }

  .docs-title-container {
    flex: 1;
  }

  #docs-branding-container {
    height: 65px;
    overflow: hidden;

    a {
      display: block;
      margin: 4px 0 4px 8px;
      padding: 8px;
    }
  }

  .goog-inline-block {
    position: relative;
    display: inline-block;
    white-space: nowrap;
    font-size: 18px;
  }

  .docs-title-input-label {
    margin: 0;
    padding: 2px 8px;
    font: 18px Arial;
    line-height: 22px;
    overflow: hidden;
    pointer-events: none;
    position: absolute;
    text-overflow: ellipsis;
    white-space: pre;
    z-index: 1;
  }

  .docs-title-widget {
    height: 27px;
    width: auto;
  }

  .docs-title-input-label-inner {
    display: inline;
    font-family: Arial;
    line-height: 22px;
    color: #777;
    font-style: italic;
    white-space: pre;
  }

  .docs-title-input {
    border: 1px solid transparent;
    border-radius: 2px;
    color: #fff;
    font-size: 18px;
    height: 20px;
    line-height: 22px;
    margin: 0;
    min-width: 1px;
    padding: 2px 7px;
    visibility: hidden;

    &:active,
    &:focus,
    &:hover {
      border-color: #e5e5e5;
    }
  }

  #docs-branding-logo {
    width: 40px;
    height: 40px;
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
    content: "";
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
