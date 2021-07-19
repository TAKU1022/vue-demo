<template>
  <article>
    <LikeHeader>
      <h2>みなさん</h2>
      <template #title="slotProps">
        <h2>こんにちわ</h2>
        <p>{{ slotProps }}</p>
      </template>
      <h3>はじめまして</h3>
      <p>よろしくお願いします</p>
      <template #number>
        <h2>{{ number }}</h2>
      </template>
    </LikeHeader>

    <LikeNumber
      :total-number="number"
      @my-click="incrementNumber($event)"
    ></LikeNumber>

    <button @click="changeComponent('Home')">Home</button>
    <button @click="changeComponent('About')">About</button>

    <keep-alive>
      <component :is="currentComponent"></component>
    </keep-alive>

    <hr />

    <div class="form-wrapper">
      <h2>イベントのフォーム</h2>

      <EventTitle v-model="eventData.title"></EventTitle>
      <!-- <EventTitle
        :value="eventData.title"
        @input="eventData.title = $event"
      ></EventTitle> -->

      <label for="maxNumber">最大人数</label>
      <input
        type="number"
        id="maxNumber"
        v-model.number="eventData.maxNumber"
      />
      <p>{{ eventData.maxNumber }}</p>

      <label for="host">主催者</label>
      <input type="text" id="host" v-model.trim="eventData.host" />
      <p>{{ eventData.host }}</p>

      <label for="detail">イベントの内容</label>
      <textarea
        id="detail"
        cols="30"
        rows="10"
        v-model="eventData.detail"
      ></textarea>
      <p style="white-space: pre">{{ eventData.detail }}</p>

      <input type="checkbox" id="isPrivate" v-model="eventData.isPrivate" />
      <label for="isPrivate">非公開</label>
      <p>{{ eventData.isPrivate }}</p>

      <div>
        <input
          type="checkbox"
          id="10"
          value="10代"
          v-model="eventData.targets"
        />
        <label for="10">10代</label>
        <input
          type="checkbox"
          id="20"
          value="20代"
          v-model="eventData.targets"
        />
        <label for="20">20代</label>
        <input
          type="checkbox"
          id="30"
          value="30代"
          v-model="eventData.targets"
        />
        <label for="30">30代</label>
        <p>{{ eventData.targets }}</p>
      </div>

      <div>
        <input type="radio" id="free" value="無料" v-model="eventData.price" />
        <label for="free">無料</label>
        <input type="radio" id="paid" value="有料" v-model="eventData.price" />
        <label for="paid">有料</label>
        <p>{{ eventData.price }}</p>
      </div>

      <select v-model="eventData.location">
        <option v-for="location in locations" :key="location">
          {{ location }}
        </option>
      </select>
      <p>{{ eventData.location }}</p>
    </div>
  </article>
</template>

<script>
  import LikeHeader from './components/LikeHeader.vue';
  import Home from './components/Home.vue';
  import About from './components/About.vue';
  import EventTitle from './components/EventTitle.vue';

  export default {
    data() {
      return {
        number: 10,
        currentComponent: 'Home',
        locations: ['東京', '大阪', '名古屋'],
        eventData: {
          title: '',
          maxNumber: 0,
          host: '',
          detail: '',
          isPrivate: false,
          targets: [],
          price: '無料',
          location: '東京',
        },
      };
    },
    components: {
      LikeHeader,
      Home,
      About,
      EventTitle,
    },
    methods: {
      incrementNumber(value) {
        this.number = value;
      },
      changeComponent(compornent) {
        this.currentComponent = compornent;
      },
    },
  };
</script>

<style lang="scss" scoped>
  article {
    border: 1px solid blue;
  }
  .form-wrapper {
    padding: 8em;
  }
</style>
