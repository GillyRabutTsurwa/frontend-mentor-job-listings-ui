<template>
  <div class="banner">
    <!-- NOTE:IMPORTANT: If you're returning a value from a function, put (). -->
    <div class="banner__logo">
      <img v-bind:src="require('../assets/images/'+ extensionString())" class="banner__logo--image" />
    </div>

    <div class="banner__work">
      <div class="banner__work--info">
        <span class="banner__work--info-company">{{itemsProp.company}}</span>
        <span class="banner__work--info-new" v-if="itemsProp.new">New!</span>
        <span class="banner__work--info-featured" v-if="itemsProp.featured">Featured!</span>
      </div>

      <p class="banner__work--title">{{itemsProp.position}}</p>

      <div class="banner__work--time-location">
        <span>{{itemsProp.postedAt}}</span>
        <span>{{itemsProp.contract}}</span>
        <span>{{itemsProp.location}}</span>
      </div>
    </div>

    <div class="banner__skills">
      <span
        v-for="(currentLanguage, index) in itemsProp.languages"
        v-bind:key="index"
      >{{currentLanguage}}</span>
      <span v-for="(currentTool) in itemsProp.tools" v-bind:key="currentTool">{{currentTool}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Banner",
  data() {
    return {
      x: this.itemsProp.logo.lastIndexOf("/")
    };
  },
  components: {},
  props: {
    itemsProp: Object
  },
  methods: {
    extensionString() {
      const extension = this.itemsProp.logo.slice(this.x + 1);
      console.log(extension);
      return extension;
    }
  },
  created() {
    console.log(this.extensionString());
  }
};
</script>

<style lang="scss">
.banner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  -webkit-box-shadow: 0px 5px 10px 0px rgba(0, 0, 0, 0.25);
  box-shadow: 0px 5px 10px 0px rgba(0, 0, 0, 0.25);
  background-color: rgb(238, 246, 246);
  margin: 4rem 0;
  padding: 4rem 2rem;

  &__logo {
    width: 6rem;
    height: 6rem;
    margin: 2rem;

    &--image {
      width: 100%;
      height: 100%;
    }
  }
  &__work {
    display: flex;
    flex-direction: column;

    & > * {
      &:not(:last-child) {
        margin-bottom: 1.25rem;
      }
    }

    &--title {
      font-size: 1.35rem;
      font-weight: 700;
    }
    &--info {
      & > * {
        margin-right: 0.5rem;
      }
      &-company {
        color: rgb(91, 164, 164);
        font-weight: 700;
        font-size: 1.125rem;
      }
      &-new,
      &-featured {
        text-transform: uppercase;
        color: rgb(238, 246, 246);
        font-weight: 700;
        padding: 0.5rem 0.75rem;
        border-radius: 1.5rem;
      }
      &-new {
        background-color: rgb(91, 164, 164);
      }
      &-featured {
        background-color: rgb(44, 58, 58);
      }
    }
    &--time-location {
      span {
        &:not(:last-child) {
          &::after {
            content: "•";
            font-size: 1.5rem;
            margin: 0 1.25rem;
          }
          // margin-right: 1rem;
        }
      }
    }
  }
  &__skills {
    margin-left: auto;

    span {
      margin-right: 1.5rem;
      padding: 0.5rem 0.75rem;
      background-color: rgba(146, 196, 196, 0.2);
      color: rgb(91, 164, 164);
      font-weight: 700;
      border-radius: 0.25rem;
    }
  }
}
</style>