<script lang="ts" setup>
import { useCounter } from '~/stores/counter'
import { useIdentity } from '~/stores/identity'
import { capitalize } from '~/utils/str'

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: capitalize(t('pages.test.title')),
  meta: [
    {
      name: 'description',
      content: t('pages.test.description'),
    },
  ],
}))
// state
const username = ref('viandwi24')
const counter = useCounter()
const identity = useIdentity()
</script>

<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle :text="$t('pages.test.title')" class="capitalize" />
    </PageHeader>
    <PageBody>
      <PageSection>
        <PageSectionTitle :text="$t('pages.test.counter')" class="capitalize" />
        <Card class="mb-4">
          <CardContent>
            <CardTitle
              class="capitalize"
              :text="$t('pages.setting.sections.validate_username.title')"
            />
            <p class="mb-2">
              {{ $t('pages.setting.sections.validate_username.description') }}
            </p>
            <div class="flex">
              <FormTextInput v-model="username" class="w-full md:w-1/3">
                <template #prefix-disabled>
                  <span class="flex-1 px-4 py-2">github.com/</span>
                </template>
              </FormTextInput>
            </div>
          </CardContent>
          <CardFooter
            class="flex flex-col space-y-2 md:space-y md:flex-row items-center md:justify-between"
          >
            <Button
              class="capitalize"
              size="sm"
              type="opposite"
              :text="
                $t('pages.setting.sections.validate_username.footer_button')
              "
            />
          </CardFooter>
        </Card>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>
