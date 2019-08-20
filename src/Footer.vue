<template>
    <b-container class="footer">
  <b-row>
    <b-col>Hey There!</b-col>
    <b-col>Contact Information</b-col>
  </b-row>
</b-container>
</template>

<style lang="scss">
@import './assets/variables.scss';
    .footer{
        background-color: $primary-background;
        height: 60px;
        min-width: 100%;
        line-height: 60px;
    }
</style>

<script>
export default {
    name: 'Footer'
}
</script>