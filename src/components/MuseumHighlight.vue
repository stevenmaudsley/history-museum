<template>
  <div class="museum-highlight position-relative">
    <icon-component class="star-five position-absolute" />
    <!-- Display the available information for the highlight -->
    <!-- Would usually use <img :src="data.image" :alt="data.title" /> if images provided -->
    <img src="@/assets/space.png" :alt="data.title" />
    <h3 class="py-3">{{ data.name }}</h3>
    <p class="museum-highlight__text">{{ text }}</p>
  </div>
</template>

<script>
import IconComponent from "@/components/Icon.vue";

export default {
  name: "MuseumHighlight",
  components: {
    IconComponent,
  },
  mixins: [],
  props: {
    data: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      text: "",
    };
  },
  computed: {
    newsDate() {
      return null;
      // Highlight's news item date
    },
  },
  methods: {
    extratctText(obj) {
      this.text = Object.getOwnPropertyDescriptor(obj, "description")
        ? obj.description
        : obj.info;
    },
  },
  created() {
    this.extratctText(this.data);
  },
};
</script>

<style lang="scss" scoped>
.star-five {
  top: 30px;
  right: 30px;
}

.museum-highlight {
  &__text {
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box !important;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    white-space: normal;
  }
}
</style>
