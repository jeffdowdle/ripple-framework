<template>
  <div class="vsba-map-popup-content">
    <h4 class="rpl-type-p-small">What's happening?</h4>

    <p
      v-if="feature.field_project_title?.length === 1"
      class="rpl-type-p-small"
    >
      {{ feature.title[0] }}
    </p>
    <RplContent v-else class="vsba-map-popup-list">
      <ul>
        <li v-for="project in feature.field_project_title" :key="project">
          {{ project }}
        </li>
      </ul>
    </RplContent>

    <p class="rpl-type-p-small rpl-u-margin-t-3">
      <RplTextLink :url="stripSiteId(feature.url[0])">
        View {{ feature.title[0] }}
      </RplTextLink>
    </p>
  </div>
</template>

<script setup lang="ts">
interface Props {
  feature: any
}
const props = withDefaults(defineProps<Props>(), {})
</script>

<style>
.vsba-map-popup-content {
  display: flex;
  flex-direction: column;
}

.vsba-map-popup-list ul {
  margin: 0;
  font-size: var(--rpl-type-size-1);
  line-height: var(--rpl-type-lh-3);
  letter-spacing: var(--rpl-type-ls-1);
}

.vsba-map-popup-list ul li:before {
  top: 0.6rem;
}
</style>
