<template>
  <div class="mainContainer">
    <div class="headerText">
      Main Values
    </div>
    <div class="subText">
      HealthX is a chance for students interested in life sciences and technology to collaborate and tackle problems in the medicine and biology field.
      <br>It was established according to our 2 main values:
    </div>
    <div class="no-overflow rows is-3-tablet">
      <div v-for="item in sortedEvents" :key="item.order">
        <div :class="{flipped: item.flipped}" class="events row">
          <div class="image-container">
            <img
              :src="item.imageLink"
              :class="{smaller: isWomenSupportingWomen(item)}"
              class="image"
            >
          </div>
          <div class="main-container">
            <h3 class="title">
              {{ item.title }}
            </h3>
            <p class="text">
              {{ item.text }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import orderBy from 'lodash.orderby'
export default {
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  computed: {
    sortedEvents: function () {
      // return orderBy(this.items, 'order')
      return [
        {
          flipped: true,
          title: 'Collaboration Between Streams',
          imageLink: require('@/assets/sprite/svg/highfive.svg'),
          text:
            "Are you an expert in neuroscience but have never touched a line of code? Perhaps you can spin up a website, but you've never heard of a mitochondria (THE POWERHOUSE OF THE CELL)? Working in diverse teams is one of the best ways to come up with unique solutions, and we encourage teams to have a blend of both technical and life science skills."
        },
        {
          title: 'Exploring New Limits',
          imageLink: require('@/assets/sprite/svg/universe.svg'),
          text:
            'HealthX is all about pushing the boundaries of what is known and unknown in the fields of medicine and life sciences. If you have an idea that you think could revolutionize the way medical research is done, or a solution that could benefit those with illnesses or disabilities, then this is the hackathon for you.'
        }
      ]
    }
  },
  methods: {
    isWomenSupportingWomen(item) {
      return item.title === 'Women* Supporting Women*'
    }
  }
}
</script>

<style lang="scss" scoped>
@import "bulma/bulma.sass";
$muted-blue: #193aa0;
$neon-blue: #78fef7;
$light-blue: #e4eeff;
$white: #ffffff;

.mainContainer {
  background-color: $muted-blue;
  padding: 0 15%;
}
.headerText {
  color: $neon-blue;
  font-family: Inter;
  font-style: normal;
  font-weight: bold;
  font-size: 42px;
  line-height: 28px;
  text-align: center;
  letter-spacing: 0.04em;
}
.subText {
  color: $white;
  font-family: Inter;
  font-style: normal;
  font-weight: normal;
  font-size: 20px;
  line-height: 35px;
  text-align: center;
  width: 67%;
  margin: 35px auto;
}
.row {
  display: flex;
  margin: 70px auto;
  &.flipped {
    flex-direction: row-reverse;
    img {
      margin: 0;
      margin-left: auto;
    }
  }
  > div {
    flex: 1;
  }
  .title {
    color: $neon-blue;
    font-family: Inter;
    font-style: normal;
    font-weight: 600;
    font-size: 30px;
    line-height: 28px;
  }
  .text {
    color: $light-blue;
    font-family: Inter;
    font-style: normal;
    font-weight: normal;
    font-size: 20px;
    line-height: 35px;
  }
  img {
    width: 388px;
    height: 263.82px;
    display: block;
    margin: 0;
    margin-right: auto;
  }
  .image-container {
    align-self: center;
  }
}
@include until($tablet) {
  .row {
    display: block;
    &.flipped {
      img {
        margin: auto;
      }
    }
    img {
      margin: auto;
    }
    .main-container {
      margin-top: 12%;
      text-align: center;
    }
  }
}
</style>
