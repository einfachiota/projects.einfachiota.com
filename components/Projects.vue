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
    console.log("this.projects", this.projects)
    }
}
</script>

<style lang="scss" scoped>
.projects {
  display: flex;
  justify-content: space-between;
  flex-wrap: nowrap;
  margin: 30px;
  margin-top: 50px;
}
@media only screen and (max-width: 920px) {
  .latest-news {
    flex-wrap: wrap;
  }
}
</style>
