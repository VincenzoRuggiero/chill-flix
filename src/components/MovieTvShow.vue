<script>
export default {
  name: "MovieTvShow",

  data() {
    return {};
  },

  props: {
    image: String,
    originalTitle: String,
    title: String,
    language: String,
    star: Number,
  },
};
</script>

<template>
  <article class="card">
    <div class="image">
      <img :src="image" :alt="title" />
    </div>

    <div class="description">
      <h2>Titolo Originale: {{ originalTitle }}</h2>

      <h4 :class="title === originalTitle ? 'd-none' : ''">
        Titolo: {{ title }}
      </h4>

      <div class="icon-flag flex">
        <span> lingua: </span>
        <img :src="language" alt="Country Flag" />
      </div>

      <div class="star flex">
        <p>Valutazione:</p>
        <p v-for="n in Math.ceil(star / 2)">
          <i class="fa-solid fa-star"></i>
        </p>
      </div>
    </div>
  </article>
</template>

<style lang="scss" scoped>
.card {
  width: calc((100% / 5) - 0.5rem);
  height: 350px;
  margin: 0 0.5rem 0.5rem 0;
  border: 1px solid white;
  background-color: black;

  &:hover .image {
    display: none;
  }

  .image {
    width: 100%;
    height: 100%;

    img {
      width: 100%;
      height: 100%;
    }
  }

  .description {
    display: none;
    color: white;
    padding: 0.5rem;
  }

  &:hover .description {
    display: block;
  }

  h2,
  h4,
  p {
    margin-bottom: 1rem;
  }
}

.icon-flag {
  width: 100px;
  height: 25px;
  align-items: center;
  margin-bottom: 1rem;

  span {
    margin-right: 1rem;
  }

  img {
    width: 100%;
    height: 100%;
  }
}

i {
  color: yellow;
}
</style>
