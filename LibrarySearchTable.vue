<template>
  <div class="search-table">
    <div>
      <Link text="Экспорт в Excel" path="#" />
      <EasyDataTableCustom
        :headers="headersMain"
        :items="itemsMain"
        :theme-color="themeColor"
        hide-footer
        class="search-table__table"
      >
        <template #header-publication="header">
          <div
            :ref="
              (el) => {
                refStorage[header.value] = el as HTMLDivElement
              }
            "
            class="search-table__custom-header"
          >
            <p>{{ header.text }}</p>
            <div
              class="search-table__dropdown-icon"
              :class="{ active: header.value === activeColumn }"
              @click="openPopup(header)"
            >
              <IconSprite name="dropdown" />
            </div>
          </div>
        </template>
        <template #header-code="header">
          <div
            :ref="
              (el) => {
                refStorage[header.value] = el as HTMLDivElement
              }
            "
            class="search-table__custom-header"
          >
            <p>{{ header.text }}</p>
            <div
              class="search-table__dropdown-icon"
              :class="{ active: header.value === activeColumn }"
              @click="openPopup(header)"
            >
              <IconSprite name="dropdown" />
            </div>
          </div>
        </template>
        <template #header-buildMode="header">
          <div
            :ref="
              (el) => {
                refStorage[header.value] = el as HTMLDivElement
              }
            "
            class="search-table__custom-header"
          >
            <p>{{ header.text }}</p>
            <div
              class="search-table__dropdown-icon"
              :class="{ active: header.value === activeColumn }"
              @click="openPopup(header)"
            >
              <IconSprite name="dropdown" />
            </div>
          </div>
        </template>
        <template #header-buildType="header">
          <div
            :ref="
              (el) => {
                refStorage[header.value] = el as HTMLDivElement
              }
            "
            class="search-table__custom-header"
          >
            <p>{{ header.text }}</p>
            <div
              class="search-table__dropdown-icon"
              :class="{ active: header.value === activeColumn }"
              @click="openPopup(header)"
            >
              <IconSprite name="dropdown" />
            </div>
          </div>
        </template>
        <template #header-name="header">
          <div
            :ref="
              (el) => {
                refStorage[header.value] = el as HTMLDivElement
              }
            "
            class="search-table__custom-header"
          >
            <p>{{ header.text }}</p>
            <div
              class="search-table__dropdown-icon"
              :class="{ active: header.value === activeColumn }"
              @click="openPopup(header)"
            >
              <IconSprite name="dropdown" />
            </div>
          </div>
        </template>
      </EasyDataTableCustom>
    </div>
    <div>
      <Link
        text="Экспорт в Excel"
        path="#"
        class="search-table__export-button"
      />
      <EasyDataTableCustom
        :headers="headersDetail"
        :items="itemsDetail"
        :theme-color="themeColor"
        hide-footer
        header-text-direction="left"
        class="search-table__table"
      >
        <template #header-param="header">
          <div
            :ref="
              (el) => {
                refStorage[header.value] = el as HTMLDivElement
              }
            "
            class="search-table__custom-header"
          >
            <p>{{ header.text }}</p>
            <div
              class="search-table__dropdown-icon"
              :class="{ active: header.value === activeColumn }"
              @click="openPopup(header)"
            >
              <IconSprite name="dropdown" />
            </div>
          </div>
        </template>
        <template #header-value="header">
          <div
            :ref="
              (el) => {
                refStorage[header.value] = el as HTMLDivElement
              }
            "
            class="search-table__custom-header"
          >
            <p>{{ header.text }}</p>
            <div
              class="search-table__dropdown-icon"
              :class="{ active: header.value === activeColumn }"
              @click="openPopup(header)"
            >
              <IconSprite name="dropdown" />
            </div>
          </div>
        </template>
      </EasyDataTableCustom>
    </div>
    <TableFilterPopup
      :is-visible="isPopupVisible"
      :row-values="popupParams.data"
      :top="popupParams.top"
      :top-shift="26"
      :left="popupParams.left"
      :left-shift="-10"
      @close="onPopupClose"
      @submit="onPopupClose"
    ></TableFilterPopup>
  </div>
</template>

<script setup lang="ts">
  import type { Header, Item } from 'vue3-easy-data-table'
  import EasyDataTableCustom from '@/components/UI/Table/EasyDataTableCustom.vue'
  import { IRefStore } from '@/components/library/libraryComponents/interfaceLibraryComponents'

  const refStorage = reactive<IRefStore>({
    publication: null,
    code: null,
    buildMode: null,
    buildType: null,
    name: null,
    param: null,
    value: null,
  })
  const themeColor = '#23527E'

  const headersMain: Header[] = [
    { text: 'Публикация', value: 'publication', width: 150 },
    { text: 'Шифр', value: 'code', width: 150 },
    { text: 'Вид строительства', value: 'buildMode' },
    { text: 'Строительный тип', value: 'buildType', width: 200 },
    { text: 'Наименование', value: 'name' },
  ]
  const itemsMain: Item[] = [
    {
      publication: 'Публикация 1',
      code: '01.01.02:001',
      buildMode: 'Жилищное строительство',
      buildType: 'Стена',
      name: 'Пилон ЖБ Монолитный 1000х180х3000',
    },
    {
      publication: 'Публикация 2',
      code: '01.01.02:002',
      buildMode: 'Жилищное строительство',
      buildType: 'Стена',
      name: 'Пилон ЖБ Монолитный 1000х180х3000',
    },
    {
      publication: 'Публикация 3',
      code: '01.01.02:003',
      buildMode: 'Жилищное строительство',
      buildType: 'Стена',
      name: 'Пилон ЖБ Монолитный 1000х180х3000',
    },
    {
      publication: 'Публикация 4',
      code: '01.01.02:004',
      buildMode: 'Жилищное строительство',
      buildType: 'Стена',
      name: 'Пилон ЖБ Монолитный 1000х180х3000',
    },
  ]

  const headersDetail: Header[] = [
    { text: 'Параметр', value: 'param', width: 150 },
    { text: 'Значение', value: 'value' },
  ]
  const itemsDetail: Item[] = [
    { param: 'Наименование', value: 'Пилон ЖБ Монолитный 1000х180х3000' },
    { param: 'Длина', value: '1000 см' },
    { param: 'Ширина', value: '180 см' },
    { param: 'Высота', value: '3000 см' },
  ]

  const activeColumn = ref<string>('')
  const isPopupVisible = ref(false)
  const popupParams = reactive<{ top: number; left: number; data: string[] }>({
    top: 0,
    left: 0,
    data: [],
  })

  const openPopup = (header: Header) => {
    if (isPopupVisible.value) return
    let rowData = []
    isPopupVisible.value = true
    activeColumn.value = header.value
    const mainColumns = headersMain.map((item) => item.value)
    const detailColumns = headersDetail.map((item) => item.value)
    if (mainColumns.includes(header.value)) {
      rowData = itemsMain.map((item) => item[header.value])
    }
    if (detailColumns.includes(header.value)) {
      rowData = itemsDetail.map((item) => item[header.value])
    }
    const rect = (
      refStorage[header.value] as HTMLElement
    )?.getBoundingClientRect()
    popupParams.top = rect?.top || 0
    popupParams.left = rect?.left || 0
    popupParams.data = rowData
  }
  const onPopupClose = () => {
    isPopupVisible.value = false
    activeColumn.value = ''
  }
</script>

<style lang="sass" scoped>
  @import 'librarySearchTable'
</style>
