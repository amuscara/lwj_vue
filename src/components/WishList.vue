<template>
  <div>
    <h1>My Wishlist boi !!!!!!!!</h1>
    <input type="text" v-model="filterText" />

    <ul :class="$style.wishlist">
      <li :key="gift.id" v-for="gift in filteredWithList">
        <h2>{{ gift.label }}</h2>
        <img :src="`/images/${gift.image}`" :alt="gift.label" />
        <p>{{ gift.votes }}</p>
        <button>wish for this</button>
      </li>
    </ul>
  </div>
</template>

<script>
import gifts from "../../public/data.json";
export default {
  data: () => ({
    gifts,
    filterText: "",
  }),
  computed: {
    filteredWithList: function() {
      return this.gifts.filter((gift) => {
        const label = gift.label.toLowerCase();
        const search = this.filterText.toLowerCase();
        return label.includes(search);
      });
    },
  },
};
</script>

<style lang="scss" module>
.wishlist {
  display: grid;
  gap: 1rem;
  grid-template-columns: repeat(auto-fit, 150px);
  grid-template-rows: auto;
  list-style: none;
  padding: 0;
  justify-content: center;

  h2 {
    font-size: 1rem;
  }

  img {
    width: 100%;
  }
}
</style>
