<template>
  <QDialog
    :value="value"
    position="top"
    @input="onInput"
  >
    <QCard>
      <QCardSection>
        <span class="text-h6">About {{ appName }}</span>
      </QCardSection>

      <QCardSection>
        <p>Version {{ appVersion }}</p>

        <p>Developed by Orientadores de Informática</p>

        <p>© 2019 Prefeitura de Mogi das Cruzes - SP</p>

        <p>
          Made with
          <QIcon name="favorite"/>
          and Quasar Framework v{{ $q.version }}
        </p>
      </QCardSection>

      <QCardActions align="right">
        <QBtn
          v-close-popup
          flat
          label="OK"
          color="primary"
        />
      </QCardActions>
    </QCard>
  </QDialog>
</template>

<script lang="ts">
import { computed, createComponent } from 'vue-function-api'

export default createComponent({
  name: 'MaeAboutDialog',
  props: {
    value: Boolean
  },
  setup (props, { emit, root }) {
    const appName = computed(() => root.$store.getters.appName)
    const appVersion = computed(() => root.$store.getters.appVersion)

    const onInput = (eventValue: boolean): void => {
      emit('input', eventValue)
    }

    return {
      appName,
      appVersion,
      onInput
    }
  }
})
</script>
