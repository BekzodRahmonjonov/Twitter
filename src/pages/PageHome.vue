<template>
  <q-page>
    <div class="q-py-lg q-px-md row items-end q-col-gutter-sm">
      <div class="col">
        <q-input 
          class="new-tweet" 
          bottom-slots 
          v-model="newTweetContent" 
          placeholder="What's happening?" 
          maxlength="280" 
          counter 
          autogrow
        >
          <template v-slot:before>
            <q-avatar size="xl">
              <img src="https://cdn.quasar.dev/img/avatar4.jpg">
            </q-avatar>
          </template>
        </q-input>
      </div>
      <div class="col col-shrink">
        <q-btn 
          :disable="!newTweetContent"
          class="q-mb-lg"
          unelevated 
          rounded 
          color="primary" 
          label="Tweet" 
          no-caps
        />
      </div>
    </div>

    <q-separator class="divider" size="10px" color="grey-2" />

    <q-list>

      <q-item class="q-py-md">
        <q-item-section avatar top>
          <q-avatar size="xl">
            <img src="https://cdn.quasar.dev/img/avatar4.jpg">
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label class="text-subtitle1">
            <strong>Bekzod Rakhmonjonov </strong>
            <span class="text-grey-7">@programmer_AI</span>
          </q-item-label>
            
          <q-item-label class="text-body1">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Lorem ipsum dolor sit amet consectetur adipisicing elit. 
            <br>
            <br>
            Aspernatur eligendi neque est, dolorem veniam, earum, ut fugiat accusantium ad odit commodi rem deleniti molestiae doloremque! Nulla veniam impedit optio! Et.Aspernatur eligendi neque est, dolorem veniam, earum, ut fugiat accusantium ad odit commodi rem deleniti molestiae doloremque! Nulla veniam impedit optio! Et.
          </q-item-label>
        </q-item-section>

        <q-item-section side top>
          1 min ago
        </q-item-section>
      </q-item>

    </q-list>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PageAbout',
  data() {
    return {
      newTweetContent: ''
    }
  },
})
</script>

<style lang="sass">
.new-tweet 
  textarea 
    font-size: 19px
    line-height: 1.4 !important
.divider
  border-top: 1px solid
  border-bottom: 1px solid
  border-color: $grey-4

</style>