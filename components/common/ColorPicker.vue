<template>
  <v-menu
    bottom
    offset-y
    :close-on-content-click="false"
  >
    <template
      v-slot:activator="{ on, attrs }"
    >
      <slot
        name="activator"
        :on="on"
        :attrs="attrs"
      />
    </template>
    <v-list>
      <v-list-item
        class="d-flex flex-column"
      >
        <v-color-picker
          class="tiptap-color-picker"
          :value="value"
          dot-size="25"
          mode="hexa"
          hide-inputs
          :swatches="swatches"
          show-swatches
          swatches-max-height="200"
          @input="val => $emit('input', val)"
        />
      </v-list-item>
    </v-list>
  </v-menu>
</template>

<script lang="ts">
import { computed, defineComponent } from '@nuxtjs/composition-api'

const swatches = [
  [
    '#BFEDD2',
    '#3EC26B',
    '#2E9179',
    '#ECF0F1',
    '#000000'
  ],
  [
    '#FBEEB8',
    '#F1C410',
    '#E67E23',
    '#CED4D9',
    '#FFFFFF'
  ],
  [
    '#F8CAC6',
    '#E03E2E',
    '#BA382A',
    '#95A5A6',
    '#00000000'
  ],
  [
    '#ECCAFA',
    '#B96AD9',
    '#843FA1',
    '#7E8C8D'
  ],
  [
    '#C2E0F4',
    '#3698DB',
    '#256FA1',
    '#34495D'
  ]
]

export default defineComponent({
  props: {
    value: {
      type: [String, Object],
      required: true
    }
  },
  setup (props) {
    const isNoColor = computed(() => props.value === '#00000000')

    return {
      swatches,
      isNoColor
    }
  }
})
</script>
