<template>
  <div class="space-page">
    <header-component class="px-1 px-md-5 py-3" />
    <h1 class="space-page__title px-5 pt-5">Space</h1>
    <!-- Add the museum highlight cards based on the data provided below -->
    <div class="d-flex flex-column flex-md-row flex-wrap">
      <museum-highlight
        v-for="(entry, i) in combinedHighights"
        :key="i"
        :data="entry"
        class="d-flex flex-column col-12 col-md-4 col-lg-3 p-5"
      />
    </div>
  </div>
</template>

<script>
import MuseumHighlight from "./MuseumHighlight";
import HeaderComponent from "./Header";

export default {
  name: "SpacePage",
  components: {
    HeaderComponent,
    MuseumHighlight,
  },
  mixins: [],
  props: {},
  data() {
    return {
      combinedHighights: [],
      sortedHighlights: [],
      spaceHighlights: [
        {
          date: "2020-04-20 12:20:00",
          description:
            "Asteroids are minor planets, especially of the inner Solar System. Larger asteroids have also been called planetoids.",
          id: 1,
          image: "",
          name: "Asteroids",
        },
        {
          date: "2020-05-20 15:50:00",
          description:
            "A comet is an icy, small Solar System body that, when passing close to the Sun, warms and begins to release gases, a process called outgassing.",
          id: 9,
          image: "",
          name: "Comets",
        },
        {
          date: "2020-05-01 9:22:00",
          description:
            "The term planet is ancient, with ties to history, astrology, science, mythology, and religion.",
          id: 7,
          image: "",
          name: "Planets",
          news: {
            date: "2020-08-18 18:00:00",
            title: "Attend our talk about Jupiter with Dr. Hogarth",
          },
          quiz: "https://planetquiz.space",
        },
        {
          date: "2020-07-05 4:10:00",
          description:
            "A meteor shower is a celestial event in which a number of meteors are observed to radiate, or originate, from one point in the night sky.",
          id: 12,
          image: "",
          name: "Meteor showers",
          news: {
            title: "The Lyrids will peak at on April 21-22 2021, at night",
          },
        },
      ],
      spacePartners: {
        observatory: {
          createdAt: "2020-06-01 11:45:00",
          info: "The Mauna Kea Observatories (MKO) are a number of independent astronomical research facilities and large telescope observatories that are located at the summit of Mauna Kea on the Big Island of Hawaiʻi, United States.",
          image: "",
          name: "Mauna Kea Observatories",
        },
      },
    };
  },
  computed: {},
  methods: {
    sortByDate(b, a) {
      const key = "date";
      let firstComparable = this.findComparable(a, key);
      let secondComparable = this.findComparable(b, key);
      return (
        new Date(secondComparable).valueOf() -
        new Date(firstComparable).valueOf()
      );
    },
    findComparable(obj, key) {
      return Object.getOwnPropertyDescriptor(obj, key)
        ? obj.date
        : obj.createdAt;
    },
  },
  created() {
    const partnerHighlights = Object.entries(this.spacePartners).map(
      (entry) => entry[1]
    );
    this.combinedHighights = [...this.spaceHighlights, ...partnerHighlights];
    this.sortedHighlights = this.combinedHighights.sort((a, b) =>
      this.sortByDate(b, a)
    );
  },
};
</script>

<style lang="scss" scoped>
.space-page {
  &__title {
    color: #2c3791;
    font-size: 24px;
    font-weight: 600;
  }
}
</style>
