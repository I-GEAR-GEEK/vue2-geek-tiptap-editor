<template>
  <v-col
    cols="auto"
  >
    <v-btn
      class="tiptap-toolbar-btn"
      :class="{
        'active': active
      }"
      small
      outlined
      v-bind="$attrs"
      v-on="$listeners"
    >
      <v-icon>
        {{ icon }}
      </v-icon>
      <slot />
    </v-btn>
    <v-divider
      v-show="hasDivider"
      vertical
    />
  </v-col>
</template>

<script lang="ts">
import { defineComponent } from '@nuxtjs/composition-api'

export default defineComponent({
  props: {
    icon: {
      type: String,
      required: true
    },
    active: {
      type: Boolean,
      default: false
    },
    hasDivider: {
      type: Boolean,
      default: false
    }
  }
})
</script>
