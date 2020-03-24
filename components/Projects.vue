<template>
  <div class="projects">
    <ProjectCard :project="project" v-for="(project, index) in projects" v-bind:key="index" />
  </div>
</template>

<script>
import ProjectCard from '@/components/ProjectCard.vue'

export default {
  name: 'Projects',
  components: {
    ProjectCard
  },
  data() {
    return {
      projects: []
    }
  },
  async created() {
      this.projects = await this.$axios.$get(process.env.projectsUrl)
    }
}
</script>

<style lang="scss" scoped>
.projects {
  display: flex;
  justify-content: space-between;
  margin: 30px auto;
  margin-top: 50px;
  width: 100%;
  flex-wrap: wrap;
  max-width: 1080px;
}
@media only screen and (max-width: 920px) {
  .projects {
    flex-wrap: wrap;
  }
}
</style>
