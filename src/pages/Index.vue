<template>
  <Layout>
    <div class="container">
      <Hero :settings="$page.settings.edges[0].node"/>
      <ProjectsGrid :projects="$page.projects.edges" />
    </div>
    <LatestJournals :journals="$page.journals.edges" />
  </Layout>
</template>

<page-query>
query Posts {
	projects: allStrapiPost {
    edges {
      node {
        id
        title
        categories {
					id
					title
				}
        thumbnail {
					url
				}
        path
      }
    }
  },
	settings: allStrapiHero {
		edges{
			node {
				footer
				site_name
				site_description
				hero_subtitle
				hero_title
				dark_mode
			}
		}
	},
  journals: allStrapiJournalPost (perPage: 4) {
    edges {
      node {
        id
        path
        title
      }
    }
  }
}
</page-query>

<script>
import Hero from "@/components/Hero"
import ProjectsGrid from "@/components/ProjectsGrid"
import LatestJournals from "@/components/LatestJournals"

export default {
  components: {
    Hero,
    ProjectsGrid,
    LatestJournals
  }
}
</script>
