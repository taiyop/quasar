<template>
  <div>
    <div id="virtual-list-scroll-target" class="scroll" style="max-height: 230px">
      <div class="q-pa-md bg-yellow">
        Above the list - scrolls with the list
      </div>

      <q-virtual-list
        class="q-my-md"
        component="q-list"
        scroll-target="#virtual-list-scroll-target"
        :items="heavyList"
        separator
      >
        <template v-slot="{ item, index }">
          <q-item
            :key="index"
            dense
          >
            <q-item-section>
              <q-item-label>
                #{{ index }} - {{ item.label }}
              </q-item-label>
            </q-item-section>
          </q-item>
        </template>
      </q-virtual-list>

      <div class="q-pa-md bg-yellow">
        Below the list - scrolls with the list
      </div>
    </div>

    <div ref="virtualListScrollTargetRef" class="scroll" style="max-height: 230px; margin-top: 40px">
      <div class="q-pa-md bg-yellow">
        Above the list - scrolls with the list
      </div>

      <q-virtual-list
        class="q-my-md"
        component="q-list"
        :scroll-target="scrollTarget"
        :items="heavyList"
        separator
      >
        <template v-slot="{ item, index }">
          <q-item
            :key="index"
            dense
          >
            <q-item-section>
              <q-item-label>
                #{{ index }} - {{ item.label }}
              </q-item-label>
            </q-item-section>
          </q-item>
        </template>
      </q-virtual-list>

      <div class="q-pa-md bg-yellow">
        Below the list - scrolls with the list
      </div>
    </div>
  </div>
</template>

<script>
const maxSize = 10000
const heavyList = []

for (let i = 0; i < maxSize; i++) {
  heavyList.push({
    label: 'Option ' + (i + 1)
  })
}

Object.freeze(heavyList)

export default {
  data () {
    return {
      heavyList,
      scrollTarget: void 0
    }
  },

  mounted () {
    this.scrollTarget = this.$refs.virtualListScrollTargetRef
  }
}
</script>
