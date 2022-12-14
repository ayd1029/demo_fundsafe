<template>
  <q-page class="q-pa-md page-default">
    <div class="row justify-center">
      <div class="col-12 doc-heading doc-h2">
        {{ $t('menu_project_modify') }}
      </div>
    </div>
    <q-separator />
    <div class="row justify-center q-pt-sm q-pb-sm">
      <div class="col-12">
        {{ $t('menu_project_modify_description') }}
      </div>
    </div>
    <div class="row justify-center q-pb-md">
    </div>

    <q-separator color="primary" style="height: 3px;" />

    <div class="row justify-center q-pt-lg">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('mainnet') }}</span>
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <q-input v-model="projectMainnet" ref="projectMainnet" standout readonly />
      </div>
    </div>

    <div class="row justify-center q-pt-lg">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_type') }}</span>
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <q-input v-model="projectType" ref="projectType" standout readonly />
      </div>
    </div>

    <div class="row justify-center q-pt-lg">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_wallet_address') }}</span>
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <q-input v-model="projectWalletAddress" ref="projectWalletAddress" standout readonly />
      </div>
    </div>

    <div class="row justify-center q-pt-lg">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_token_contract_address') }}</span>
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <q-input v-model="projectTokenContractAddress" ref="projectTokenContractAddress" standout readonly />
      </div>
    </div>

    <div class="row justify-center q-pt-lg">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_platform_contract_address') }}</span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectPlatformContractAddress" ref="projectPlatformContractAddress" standout readonly />
      </div>
    </div>
    <br />

    <q-separator color="primary" style="height: 3px;" />

    <div class="row justify-center q-pt-lg">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_title') }} (English)<span class="text-red"> *</span></span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectTitle" ref="projectTitle" :rules="[required, val => minLength(val, 1), val => maxLength(val, 50)]" clearable standout tabindex="1" />
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_title') }} (Korean)<span class="text-red"> *</span></span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectTitleKo" ref="projectTitleKo" :rules="[required, val => minLength(val, 1), val => maxLength(val, 50)]" clearable standout tabindex="2" />
      </div>
    </div>

    <q-separator color="primary" style="height: 3px;" />

    <div class="row justify-center q-pt-lg">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_summary') }} (English)<span class="text-red"> *</span></span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectSummary" ref="projectSummary" :rules="[required, val => minLength(val, 1), val => maxLength(val, 100)]" clearable standout tabindex="3" />
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_summary') }} (Korean)<span class="text-red"> *</span></span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectSummaryKo" ref="projectSummaryKo" :rules="[required, val => minLength(val, 1), val => maxLength(val, 100)]" clearable standout tabindex="4" />
      </div>
    </div>

    <q-separator color="primary" style="height: 3px;" />

    <div class="row justify-center q-pt-lg">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_description') }} (English)<span class="text-red"> *</span></span>
      </div>
    </div>
    <div class="row justify-center q-pb-lg">
      <div class="col-12">
        <q-editor
          v-model="projectDescription"
          min-height="10rem"
          autofocus
          tabindex="5"
          @keyup.enter.stop
          toolbar-bg="grey-1"
          :toolbar="[
            ['left', 'center', 'right', 'justify'],
            ['bold', 'italic', 'strike', 'underline', 'subscript', 'superscript'],
            ['token', 'hr', 'link', 'custom_btn'],
            [
              {
                label: $q.lang.editor.formatting,
                icon: $q.iconSet.editor.formatting,
                list: 'no-icons',
                options: [
                  'p',
                  'h1',
                  'h2',
                  'h3',
                  'h4',
                  'h5',
                  'h6',
                  'code'
                ]
              },
              {
                label: $q.lang.editor.fontSize,
                icon: $q.iconSet.editor.fontSize,
                fixedLabel: true,
                fixedIcon: true,
                list: 'no-icons',
                options: [
                  'size-1',
                  'size-2',
                  'size-3',
                  'size-4',
                  'size-5',
                  'size-6',
                  'size-7'
                ]
              },
              {
                label: $q.lang.editor.defaultFont,
                icon: $q.iconSet.editor.font,
                fixedIcon: true,
                list: 'no-icons',
                options: [
                  'default_font',
                  'arial',
                  'arial_black',
                  'comic_sans',
                  'courier_new',
                  'impact',
                  'lucida_grande',
                  'times_new_roman',
                  'verdana'
                ]
              },
              'removeFormat'
            ],
            ['quote', 'unordered', 'ordered', 'outdent', 'indent'],

            ['undo', 'redo'],
            ['print', 'fullscreen'],
            ['viewsource']
          ]"
          :fonts="{
            arial: 'Arial',
            arial_black: 'Arial Black',
            comic_sans: 'Comic Sans MS',
            courier_new: 'Courier New',
            impact: 'Impact',
            lucida_grande: 'Lucida Grande',
            times_new_roman: 'Times New Roman',
            verdana: 'Verdana'
          }"
        />
      </div>
    </div>
    <div class="row justify-center q-pt-sm">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_description') }} (Korean)<span class="text-red"> *</span></span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-editor
          v-model="projectDescriptionKo"
          min-height="10rem"
          autofocus
          tabindex="6"
          @keyup.enter.stop
          toolbar-bg="grey-1"
          :toolbar="[
            ['left', 'center', 'right', 'justify'],
            ['bold', 'italic', 'strike', 'underline', 'subscript', 'superscript'],
            ['token', 'hr', 'link', 'custom_btn'],
            [
              {
                label: $q.lang.editor.formatting,
                icon: $q.iconSet.editor.formatting,
                list: 'no-icons',
                options: [
                  'p',
                  'h1',
                  'h2',
                  'h3',
                  'h4',
                  'h5',
                  'h6',
                  'code'
                ]
              },
              {
                label: $q.lang.editor.fontSize,
                icon: $q.iconSet.editor.fontSize,
                fixedLabel: true,
                fixedIcon: true,
                list: 'no-icons',
                options: [
                  'size-1',
                  'size-2',
                  'size-3',
                  'size-4',
                  'size-5',
                  'size-6',
                  'size-7'
                ]
              },
              {
                label: $q.lang.editor.defaultFont,
                icon: $q.iconSet.editor.font,
                fixedIcon: true,
                list: 'no-icons',
                options: [
                  'default_font',
                  'arial',
                  'arial_black',
                  'comic_sans',
                  'courier_new',
                  'impact',
                  'lucida_grande',
                  'times_new_roman',
                  'verdana'
                ]
              },
              'removeFormat'
            ],
            ['quote', 'unordered', 'ordered', 'outdent', 'indent'],

            ['undo', 'redo'],
            ['print', 'fullscreen'],
            ['viewsource']
          ]"
          :fonts="{
            arial: 'Arial',
            arial_black: 'Arial Black',
            comic_sans: 'Comic Sans MS',
            courier_new: 'Courier New',
            impact: 'Impact',
            lucida_grande: 'Lucida Grande',
            times_new_roman: 'Times New Roman',
            verdana: 'Verdana'
          }"
        />
      </div>
    </div>
    <br />

    <q-separator color="primary" style="height: 3px;" />

    <div class="row justify-center q-pt-lg">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_official_website') }}</span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectOfficialWebsite" ref="projectOfficialWebsite" :rules="[val => maxLength(val, 100)]" clearable standout tabindex="7" placeholder="e.g. https://klayswap.com" />
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_official_email') }}<span class="text-red"> *</span></span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectOfficialEmail" ref="projectOfficialEmail" :rules="[required, val => minLength(val, 5), val => maxLength(val, 30)]" clearable standout tabindex="8" />
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_logo_image') }}</span>
        <span class="text-grey">
          &nbsp;&nbsp;({{ $t('image_reset') }} : <q-icon name="done_all" size="sm" />)
        </span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-uploader
          field-name="file"
          ref="uploaderObj"
          url="/api/common/uploadImage"
          hide-upload-btn
          color="grey-3"
          text-color="black"
          :multiple="false"
          accept="image/*"
          :filter="filterFiles"
          max-files="1"
          :auto-upload="true"
          tabindex="9"
          @uploaded="fileUploaded"
        />
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12 text-red text-bold">
        {{ $t('square_image_only') }}
      </div>
    </div>

    <!-- preview -->
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">??? {{ $t('preview') }}</span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-card class="my-card">
          <q-item>
            <q-item-section avatar>
              <q-avatar>
                <img v-if="projectLogoImage" :src="projectLogoImage">
                <q-icon v-else name="rocket_launch" size="md" />

              </q-avatar>
            </q-item-section>

            <q-item-section>
              <div class="row">
                <q-item-label class="col-12">{{ projectTitle }}</q-item-label>
                <q-item-label class="col-12">{{ projectSummary }}</q-item-label>
              </div>
            </q-item-section>
          </q-item>
        </q-card>
      </div>
    </div>
    <br />

    <q-separator color="primary" style="height: 3px;" />

    <div class="row justify-center q-pt-lg">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_docs') }}</span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectDocs" ref="projectDocs" :rules="[val => maxLength(val, 100)]" clearable standout tabindex="10" placeholder="e.g. https://docs.klayswap.com" />
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_blog') }}</span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectBlog" ref="projectBlog" :rules="[val => maxLength(val, 100)]" clearable standout tabindex="11" placeholder="e.g. https://medium.com/iotrustlab/tagged/klayswap" />
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_medium') }}</span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectMedium" ref="projectMedium" :rules="[val => maxLength(val, 100)]" clearable standout tabindex="12" placeholder="e.g. https://medium.com/klayswap" />
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_telegram') }}</span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectTelegram" ref="projectTelegram" :rules="[val => maxLength(val, 100)]" clearable standout tabindex="13" placeholder="e.g. https://t.me/klayswapchannel" />
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_twitter') }}</span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectTwitter" ref="projectTwitter" :rules="[val => maxLength(val, 100)]" clearable standout tabindex="14" placeholder="e.g. https://twitter.com/KLAYswap" />
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_github') }}</span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectGithub" ref="projectGithub" :rules="[val => maxLength(val, 100)]" clearable standout tabindex="15" placeholder="e.g. https://github.com/KlaySwap" />
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_meta') }}</span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectMeta" ref="projectMeta" :rules="[val => maxLength(val, 100)]" clearable standout tabindex="16" placeholder="e.g. https://www.facebook.com/klayswap" />
      </div>
    </div>
    <div class="row justify-center">
      <div class="col-12">
        <span class="text-weight-bold text-subtitle1">{{ $t('project_discord') }}</span>
      </div>
    </div>
    <div class="row justify-center q-pb-md">
      <div class="col-12">
        <q-input v-model="projectDiscord" ref="projectDiscord" :rules="[val => maxLength(val, 100)]" clearable standout tabindex="17" placeholder="e.g. https://discord.gg/fRhThwHXGQ" />
      </div>
    </div>

    <div class="row justify-center q-pt-md">
      <div class="col-6 text-left">
        <q-btn class="btn" color="grey-3" text-color="black" size="lg" style="width: 98%;" @click="goBack" tabindex="19">
          <b>{{ $t('go_back') }}</b>
        </q-btn>
      </div>
      <div class="col-6 text-right">
        <q-btn class="btn" color="secondary" text-color="black" size="lg" style="width: 98%;" @click="modifyProject" tabindex="18">
          <b>{{ $t('modify') }}</b>
        </q-btn>
      </div>
    </div>

    <!-- ?????? ?????? ?????? -->
    <div class="row justify-center q-pa-xl">
    </div>

  </q-page>

  <WalletModal ref="refWalletModal" />

  <q-dialog v-model="confirmGoBack">
    <q-card>
      <q-card-section class="row items-center" style="min-width: 200px;">
        <!-- <q-avatar icon="warning" color="primary" text-color="white" size="sm" /> -->
        <q-icon name="warning" color="primary" size="md" />
        <span class="q-ml-sm">{{ $t('confirm_go_back') }}</span>
      </q-card-section>
      <q-separator />
      <q-card-actions align="around">
        <q-btn flat style="width: 45%;" :label="$t('cancel')" color="black" v-close-popup />
        <q-btn flat style="width: 45%;" :label="$t('go_back')" color="black" v-close-popup @click="doGoBack" />
      </q-card-actions>
    </q-card>
  </q-dialog>

</template>

<script>
import { defineComponent } from 'vue';
import { required, requiredNumber, minLength, maxLength, minValue, maxValue} from 'src/validation.js';

export default defineComponent({
  name: 'ModifyProject',
  data () {
    return {
      projectSeq: '', // route parameter seq
      projectMainnet: '',
      projectType: '',
      projectTitle: '',
      projectTitleKo: '',
      projectSummary: '',
      projectSummaryKo: '',
      projectDescription: '',
      projectDescriptionKo: '',
      projectOfficialWebsite: '',
      projectOfficialEmail: '',
      projectLogoImage: '',
      projectDocs: '',
      projectBlog: '',
      projectMedium: '',
      projectTelegram: '',
      projectTwitter: '',
      projectGithub: '',
      projectMeta: '',
      projectDiscord: '',
      projectWalletAddress: '',
      projectTokenContractAddress: '',
      projectPlatformContractAddress: '',
      // seqFileMst: '' // ?????? ????????? SEQ
      confirmGoBack: false, // goBack ?????????
    }
  },
  components: {
  },
  computed: {
    getUid () {
      return this.$store.getters.getUid
    }
  },
  created: function () {
    // ??? ??????
    this.projectSeq = this.$route.query.seq
    // ???????????? ?????? ??????
    this.selectProject()
  },
  mounted: function () {},
  methods: {
    // ???????????? ??????
    selectProject() {
      const param = {
        uid: this.getUid,
        seq: this.projectSeq,
      }

      // ???????????? ??????
      this.$axios.get('/api/project/selectProject', { params: { ...param }})
        .then((result) => {
          // console.log(JSON.stringify(result.data))
          if (result.data) {
            // console.log(result.data)
            this.projectMainnet = result.data.mainnet
            this.projectType = result.data.type
            this.projectTitle = result.data.title
            this.projectTitleKo = result.data.title_ko
            this.projectSummary = result.data.summary
            this.projectSummaryKo = result.data.summary_ko
            this.projectDescription = result.data.description
            this.projectDescriptionKo = result.data.description_ko
            this.projectOfficialWebsite = result.data.official_website
            this.projectOfficialEmail = result.data.official_email
            this.projectLogoImage = result.data.logo_image
            this.projectDocs = result.data.docs
            this.projectBlog = result.data.blog
            this.projectMedium = result.data.medium
            this.projectTelegram = result.data.telegram
            this.projectTwitter = result.data.twitter
            this.projectGithub = result.data.github
            this.projectMeta = result.data.meta
            this.projectDiscord = result.data.discord
            this.projectWalletAddress = result.data.wallet_address
            this.projectTokenContractAddress = result.data.token_contract_address
            this.projectPlatformContractAddress = result.data.platform_contract_address
          } else {
            this.$noti(this.$q, this.$t('request_data_failed'))
          }
        })
        .catch((err) => {
          console.log(err)
        })
    },
    callbackLogin(userVo) {
      // console.log('callbackLogin!!!')
      this.$store.dispatch('setUid', userVo.uid)
      this.$store.dispatch('setAdcd', userVo.adcd)
      this.$store.dispatch('setName', userVo.name)
      this.$store.dispatch('setNickname', userVo.nickname)
      this.$store.dispatch('setProfileImage', userVo.profile_image)
      this.$store.dispatch('setWalletType', userVo.wallet_type)
      this.$store.dispatch('setWalletAddress', userVo.wallet_address)
      this.$store.dispatch('setMobileNo', userVo.mobile_no)
    },
    ///////////////////////////////////////////////////////////////////////////
    // validation
    ///////////////////////////////////////////////////////////////////////////
    required(val) {
      const message = this.$t('validation_required')
      return required(val, message);
    },
    requiredNumber(val) {
      const message = this.$t('validation_required')
      return required(val, message);
    },
    minLength(val, length) {
      if (!val) {
        return true
      }
      const message = this.$t('validation_min_length') + ': ' + length
      return minLength(val, message, length);
    },
    maxLength(val, length) {
      if (!val) {
        return true
      }
      const message = this.$t('validation_max_length') + ': ' + length
      return maxLength(val, message, length);
    },
    minValue(val, value) {
      const message = this.$t('validation_min_value') + ': ' + value
      return minValue(val, message, value);
    },
    maxValue(val, value) {
      const message = this.$t('validation_max_value') + ': ' + value
      return maxValue(val, message, value);
    },
    ///////////////////////////////////////////////////////////////////////////
    validate() {
      let result = true
      if (!this.$refs.projectTitle.validate()) {
        result = false
      }
      if (!this.$refs.projectTitleKo.validate()) {
        result = false
      }
      if (!this.$refs.projectSummary.validate()) {
        result = false
      }
      if (!this.$refs.projectSummaryKo.validate()) {
        result = false
      }
      if (!this.$refs.projectOfficialWebsite.validate()) {
        result = false
      }
      if (!this.$refs.projectOfficialEmail.validate()) {
        result = false
      }
      if (!this.$refs.projectDocs.validate()) {
        result = false
      }
      if (!this.$refs.projectBlog.validate()) {
        result = false
      }
      if (!this.$refs.projectMedium.validate()) {
        result = false
      }
      if (!this.$refs.projectTelegram.validate()) {
        result = false
      }
      if (!this.$refs.projectTwitter.validate()) {
        result = false
      }
      if (!this.$refs.projectGithub.validate()) {
        result = false
      }
      if (!this.$refs.projectMeta.validate()) {
        result = false
      }
      if (!this.$refs.projectDiscord.validate()) {
        result = false
      }
      return result
    },
    // ???????????? ?????? ?????? ??????
    async modifyProject() {
      // Field validation check
      if(!this.validate()) {
        this.$noti(this.$q, this.$t('validation_failed'))
        return
      }

      // ????????? ?????? ??????, ????????? ?????? ??????
      if (!this.getUid) {
        this.$refs.refWalletModal.show()
        return
      }

      // ???????????? ??????
      this.doModifyProject()
    },
    // ???????????? ??????
    async doModifyProject() {
      // 1. ???????????? ?????? ??????
      const params = {
        uid: this.getUid,
        seq: this.projectSeq,
        title: this.projectTitle,
        title_ko: this.projectTitleKo,
        summary: this.projectSummary,
        summary_ko: this.projectSummaryKo,
        description: this.projectDescription,
        description_ko: this.projectDescriptionKo,
        official_website: this.projectOfficialWebsite,
        official_email: this.projectOfficialEmail,
        logo_image: this.projectLogoImage,
        docs: this.projectDocs,
        blog: this.projectBlog,
        medium: this.projectMedium,
        telegram: this.projectTelegram,
        twitter: this.projectTwitter,
        github: this.projectGithub,
        meta: this.projectMeta,
        discord: this.projectDiscord,
      }
      this.$q.loading.show() // ?????? ?????? ??????
      this.$axios.post('/api/project/updateProject', params)
        .then((result) => {
          // console.log(JSON.stringify(result.data))
          this.$q.loading.hide() // ?????? ?????? ??????
          if (result.data && result.data.resultCd === 'SUCCESS') {
            // console.log(result.data)
            this.$noti(this.$q, this.$t('modify_success'))

            // // ????????? ??????
            this.$router.go(-1)
            // if (this.$route.query.fromAdmin === 'Y') {
            //   // ?????? ???????????? ????????? ?????? - admin
            //   this.$router.push('/admin/adminMyList')
            // } else {
            //   // ?????? ???????????? ????????? ??????
            //   this.$router.push('/project/myList')
            // }
            // <!-- ????????? ????????? -->
            // this.$router.push('/project/newList')
          } else {
            this.$noti(this.$q, this.$t('modify_failed'))
          }
        })
        .catch((err) => {
          this.$q.loading.hide() // ?????? ?????? ??????
          console.log(err)
          this.$noti(this.$q, err)
        })
    },
    // ?????? ????????? ??????
    filterFiles (files) {
      const MAX_FILE_SIZE = 2 * 1024 * 1024
      // this.$store.state.UPLOAD_FILE_SIZE_LIMIT * 1024 * 1024 // = 4M
      // returns an Array containing allowed files
      return files.filter((file) => {
        if (file.size > MAX_FILE_SIZE) {
          this.$noti(this.$q, this.$t('file_size_exceeded'))

        }
        return file.size <= MAX_FILE_SIZE
      })
    },
    // fileAdded (files) {
    //   // this.$refs.uploaderObj.reset()
    //   this.$refs.uploaderObj.removeUploadedFiles()
    //   this.$refs.uploaderObj.upload()
    // },
    fileUploaded (file, xhr) {
      // ????????? ???????????? ???????????? ???????????? ?????????
      // let fileName = file.name
      // let fileSize = file.size
      // let fileType = file.type
      let fileNameNew = file.xhr.responseText
      // console.log('fileName: ' + fileName)
      // console.log('fileSize: ' + fileSize)
      // console.log('fileType: ' + fileType)
      console.log('fileNameNew: ' + fileNameNew)

      this.projectLogoImage = fileNameNew // ???????????? ?????? URL ??????
      // this.$refs.uploaderObj.reset()
    },
    goBack() {
      // this.$router.go(-1)

      // goBack ????????? ??????
      this.confirmGoBack = true
    },
    doGoBack() {
      // ????????? ??????
      this.$router.go(-1)
      // if (this.$route.query.fromAdmin === 'Y') {
      //   // ?????? ???????????? ????????? ?????? - admin
      //   this.$router.push('/admin/adminMyList')
      // } else {
      //   // ?????? ???????????? ????????? ??????
      //   this.$router.push('/project/myList')
      // }
    }
  }
})
</script>

<style scoped>
</style>
