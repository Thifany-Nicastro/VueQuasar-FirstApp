<template>
  <div class="q-pa-md">
    <q-table
      title="Treats"
      :rows="rows"
      :columns="columns"
      row-key="name"
      :selected-rows-label="getSelectedString"
      selection="multiple"
      v-model:selected="selected"
    />

    <div class="q-mt-md">
      Selected: {{ JSON.stringify(selected) }}
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

const columns = [
  {
    name: 'desc',
    required: true,
    label: 'Dessert (100g serving)',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true
  },
  { name: 'calories', align: 'center', label: 'Calories', field: 'calories', sortable: true },
  { name: 'fat', label: 'Fat (g)', field: 'fat', sortable: true },
]

const rows = [
  {
    name: 'Frozen Yogurt',
    calories: 159,
    fat: 6.0,
  },
  {
    name: 'Ice cream sandwich',
    calories: 237,
    fat: 9.0,
  },
  {
    name: 'Eclair',
    calories: 262,
    fat: 16.0,
  },
  {
    name: 'Cupcake',
    calories: 305,
    fat: 3.7,
  },
  {
    name: 'Gingerbread',
    calories: 356,
    fat: 16.0,
  },
  {
    name: 'Jelly bean',
    calories: 375,
    fat: 0.0,
  },
  {
    name: 'Lollipop',
    calories: 392,
    fat: 0.2,
  },
  {
    name: 'Honeycomb',
    calories: 408,
    fat: 3.2,
  },
  {
    name: 'Donut',
    calories: 452,
    fat: 25.0,
  },
  {
    name: 'KitKat',
    calories: 518,
    fat: 26.0,
  }
]

export default {
  setup () {
    const selected = ref([])

    return {
      selected,
      columns,
      rows,

      getSelectedString () {
        return selected.value.length === 0 ? '' : `${selected.value.length} record${selected.value.length > 1 ? 's' : ''} selected of ${rows.length}`
      }
    }
  }
}
</script>

<style>

</style>