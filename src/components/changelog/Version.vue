<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">
        {{version.id}}
      </p>
    </header>
    <div class="card-content">
      <div class="content">
        <ul>
          <li v-for="change in version.changes" :key="change.date">
            {{change}}
          </li>
        </ul>
      </div>
    </div>
    <div class="card-footer">
      <p class="card-footer-item has-text-centered-mobile">
        Release Date: {{version.date}}
      </p>
      <p class="card-footer-item">
        <a :href="release_url" class="button">
          <span class="icon">
            <github-box/>
          </span>
          <span>Release</span>
        </a>
      </p>
    </div>
  </div>
</template>

<script>
import GithubBox from 'mdi-vue/GithubBoxIcon'
export default {
  name: 'version',
  components: {
    GithubBox
  },
  props: {
    version: {
      type: Object,
      default () {
        return {
          id: 'Version 1.0',
          date: '2016-04-13',
          link: 'Version-1.0',
          changes: [
            'Initial Version'
          ]
        }
      }
    }
  },
  computed: {
    release_url () {
      return 'https://github.com/kihashi/stardew_community_checklist/releases/tag/' + this.version.link
    }
  }

}
</script>

<style>

</style>
