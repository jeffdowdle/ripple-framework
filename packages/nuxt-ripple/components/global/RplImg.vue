<script setup lang="ts">
import useProviderImage from '../../composables/use-provider-image'
import { computed } from 'vue'

interface Props {
  src: string
  alt: string
  width?: number | undefined
  height?: number | undefined
  aspect?: any
  srcSet?: string
  sizes?: any
}

const props = withDefaults(defineProps<Props>(), {
  width: undefined,
  height: undefined,
  aspect: undefined,
  srcSet: undefined,
  sizes: undefined
})

// Composable handles all the logic for determining the correct image to use
const { providerSrcSet, providerSizes } = useProviderImage(props)

const initialSrc = computed(
  () => `${props.src}?w=${props.width * 2 < 1984 ? props.width * 2 : 1984}`
)
</script>

<template>
  <img
    :src="initialSrc"
    :srcSet="providerSrcSet"
    :sizes="providerSizes"
    :width="width"
    :height="height"
    :alt="alt || ''"
  />
</template>
