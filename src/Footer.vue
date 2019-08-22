<template>
  <b-container class="footer">
    <b-row class="footer-info">
      <b-col sm="12" md="4" offset-md="2">
        <h2>Hey There!</h2>
        <p>Please feel free to get in touch with me! I'd love to chat over some coffee or bbt tea!</p>
        <div>
          <b-button-group>
            <b-button><a href="https://www.instagram.com/estelledes/" target="_blank"><img src="../public/img/SVG/instagram.svg"></a></b-button>
            <b-button><a href="https://www.linkedin.com/in/estelle-chung/" target="_blank"><img src="../public/img/SVG/linkedin2.svg"></a></b-button>
            <b-button><a href="https://github.com/estelledes" target="_blank"><img src="../public/img/SVG/github.svg"></a></b-button>
            <!-- <b-button><a><img src="../public/img/SVG/twitter.svg"></a></b-button> -->
            <!-- <b-button><img src="../public/img/SVG/behance.svg"></b-button> -->
            <!-- <b-button><img src="../public/img/SVG/dribble.svg"></b-button> -->
          </b-button-group>
        </div>
      </b-col>
      <b-col sm="12" md="4">
        <h2>Contact Information</h2>
        <ul>
          <li>Toronto, ON</li>
          <li>+ 647 526 2866</li>
          <li>
            <a href="mailto:me@estellechung.com">me@estellechung.com</a>
          </li>
        </ul>
        <p></p>
      </b-col>
    </b-row>
  </b-container>
</template>

<style lang="scss">
@import "./assets/variables.scss";

.btn {
  padding-left: 0 !important;

  width:40px;
  img{
    border-radius: 0;
  }
}
.btn-secondary{
  background-color: transparent !important;
  border-color: transparent !important;
}
.footer {
  background-color: white;
  height: auto;
  min-width: 100%;
  text-align: left;
  h2 {
    font-size: 24px;
  }
  .footer-info {
    padding-top: 3vh;
    padding-bottom: 3vh;
  }
  .description {
    padding-left: 20vh;
  }
  p {
    line-height: 18px;
  }
  ul {
    list-style-type: none;
    line-height: 30px;
    padding-left: 0px;
  }
}
</style>

<script>
export default {
  name: "Footer"
};
</script>
