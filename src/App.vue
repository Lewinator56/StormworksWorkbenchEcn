<template>
 <q-layout view="lHh lpr lFf" container style="height: 100vh" class="shadow-2">
      <q-header elevated>

        <div class="q-pa-sm q-pl-md row items-center">
          <div class="cursor-pointer non-selectable">
            File
            <q-menu>
              <q-list dense style="min-width: 100px">
                <q-item clickable v-close-popup>
                  <q-item-section>Open...</q-item-section>
                </q-item>
                <q-item clickable v-close-popup>
                  <q-item-section>New</q-item-section>
                </q-item>

                <q-separator />

                <q-item clickable v-close-popup>
                  <q-item-section>Save</q-item-section>
                </q-item>
                <q-item clickable v-close-popup>
                  <q-item-section>Save As</q-item-section>
                </q-item>
                

                <q-separator />

                <q-item clickable v-close-popup>
                  <q-item-section>Quit</q-item-section>
                </q-item>
              </q-list>
            </q-menu>
          </div>

          <div class="q-ml-md cursor-pointer non-selectable">
            Edit
            <q-menu auto-close>
              <q-list dense style="min-width: 100px">
                <q-item clickable>
                  <q-item-section>Cut</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Copy</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Paste</q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable>
                  <q-item-section>Select All</q-item-section>
                </q-item>
              </q-list>
            </q-menu>
          </div>

          <div class="q-ml-md cursor-pointer non-selectable">
            View
            <q-menu auto-close>
              <q-list dense style="min-width: 100px">
                <q-item clickable>
                  <q-item-section>Show Start page</q-item-section>
                </q-item>
              </q-list>
            </q-menu>
          </div>

           <div class="q-ml-md cursor-pointer non-selectable">
            Project
            <q-menu auto-close>
              <q-list dense style="min-width: 100px;">
                <q-item clickable>
                  <q-item-section>Publish</q-item-section>
                </q-item>

                <q-separator />

                <q-item clickable>
                  <q-item-section>Import Mesh</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>IMport Obj</q-item-section>
                </q-item>


              </q-list>
            </q-menu>
          </div>

          <div class="q-ml-md cursor-pointer non-selectable">
            Plugins
            <q-menu auto-close>
              <q-list dense style="min-width: 100px">
                <q-item clickable>
                  <q-item-section>Load Plugin</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Manage Plugins</q-item-section>
                </q-item>

                <q-separator />

                <!-- list plugins here -->


              </q-list>
            </q-menu>
          </div>
        </div>
      </q-header>

      <q-page-container style="height: 100vh">
        <splitpanes  horizontal style="height: 100%">
          <pane size="75">
            <splitpanes  vertical style="height: 100%">
              <pane size="25">
                <div></div>
              </pane>
              <pane size="75">
                <div></div>
              </pane>
              </splitpanes>
          </pane>
          <pane size="25" min-size="5">
            <div>
              <q-tabs v-model="tab" dense inline-label align="left" class="bg-primary text-white shadow-2" >
                <q-tab label="Console" name="Console" icon="terminal">
                  <div></div>
                </q-tab>
                <q-tab  label= "outut" name="Output" icon="output">
                  <div></div>
                </q-tab>
              </q-tabs>
            </div>
          </pane>
        </splitpanes>
      </q-page-container>
    </q-layout>


</template>

<style lang="sass">

@import 'styles/quasar.sass'

q-menu 
  background-color: $primary
.splitpanes__pane 
  background-color: $dark

.splitpanes--vertical > .splitpanes__splitter 
  min-width: 1px
  background: #4f5b62


.splitpanes--horizontal > .splitpanes__splitter 
  min-height: 1px
  background: #4f5b62

.splitpanes__splitter
  position: relative

.splitpanes__splitter:before 
  content: ''
  position: absolute
  left: 0
  top: 0
  

.splitpanes__splitter:hover:before 
  opacity: 1
.splitpanes--vertical > .splitpanes__splitter:before 
  left: -5px
  right: -5px
  height: 100%
.splitpanes--horizontal > .splitpanes__splitter:before 
  top: -5px
  bottom: -5px
  width: 100%


</style>

<script>
import { ref } from 'vue'
import { useQuasar } from 'quasar'
import { Splitpanes, Pane } from 'splitpanes'
import 'splitpanes/dist/splitpanes.css'


export default {
  name: 'LayoutDefault',

  components: {
    Splitpanes, Pane
  },

  setup () {

    const $q = useQuasar()
    

    // calling here; equivalent to when component is created
    $q.dark.set(true)
    return {
      leftDrawerOpen: ref(false),
      tab: ref('output')
    }
  }
}
</script>
