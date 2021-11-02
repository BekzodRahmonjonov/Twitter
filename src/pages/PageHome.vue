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
          @click="addNewTweet"
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

      <q-item
        class="q-py-md"
        v-for="tweet in tweets"
        :key="tweet.date"
      >
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
            {{ tweet.description }}
            <br>
            <br>
            {{ tweet.content }}
          </q-item-label>
          <div class="tweet-icons row justify-between q-mt-sm">
            <q-btn flat round color="grey" icon="far fa-comment" size="sm" />
            <q-btn flat round color="grey" icon="fas fa-retweet" size="sm" />
            <q-btn flat round color="grey" icon="far fa-heart" size="sm" />
            <q-btn @click="deleteTweet(tweet)" flat round color="grey" icon="fas fa-trash" size="sm" />
          </div>
        </q-item-section>

        <q-item-section side top>
          {{ tweet.date | relativeDate }}
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';
import { formatDistance } from 'date-fns'

export default defineComponent({
  name: 'PageAbout',
  data() {
    return {
      newTweetContent: '',
      tweets: [
        {
          content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Dignissimos consectetur, accusantium fugit similique explicabo deserunt temporibus, sed tenetur, vel iure nostrum. Est nam dolor repellendus aut? Reiciendis tenetur cumque molestiae.',
          description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit.',
          date: 1635608924781,
        },
        {
          content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Dignissimos consectetur, accusantium fugit similique explicabo deserunt temporibus, sed tenetur, vel iure nostrum. Est nam dolor repellendus aut? Reiciendis tenetur cumque molestiae.',
          description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit.',
          date: 1635608973632,
        }
      ],
    }
  },
  methods: {
    addNewTweet() {
      let newTweet = {
        content: this.newTweetContent,
        date: Date.now()
      }
      this.tweets.unshift(newTweet)
    },
    deleteTweet(tweet) {
      let dateToDelete = tweet.date
      let index = this.tweets.findIndex(tweet => tweet.date === dateToDelete)
      this.tweets.splice(index, 1)
    }
  },
  filters: {
    relativeDate(value) {
      return formatDistance(value, new Date())
    }
  }
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
.tweet-icons
  margin-left: -5px
</style>
