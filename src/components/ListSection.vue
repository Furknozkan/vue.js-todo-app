<template>
<div>
  
  <ListItemSection  />
  <ListDetailSection />
  </div>
</template>
<script>
import ListItemSection from "@/components/ListItemSection"
import ListDetailSection from "@/components/ListDetailSection"
export default {
  
    components: {
        ListItemSection,
        ListDetailSection
    }
}
</script>