<template>
  <div class="component-box">
    <div class="description-box">
      <span class="title-text">Our Newsletter</span>
      <span class="description-text"
        >Tamen quem nulla quae legam multos aute sint culpa legam noster
        magna</span
      >
    </div>
    <div style="display: flex; margin-top: 40px;">
      <input type="text" class="email-input" />
      <button class="button">Subscribe</button>
    </div>
  </div>
</template>

<script>
export default {}
</script>
<style scoped>
.component-box {
  display: flex;
  flex-direction: row;
  height: 172px;
  background-color: #2e3339;
  align-items: center;
  justify-content: center;
  padding-inline: 20px;
}
.description-box {
  display: flex;
  flex-direction: column;
}
.description-text {
  font-size: 14px;
  font-family: 'Open Sans', sans-serif;
  font-weight: 400;
  line-height: 1.5;
  color: #ffffff;
}
.title-text {
  font-family: 'Raleway', sans-serif;
  font-size: 24px;
  line-height: 1;
  font-weight: 600;
  color: #ffffff;
  margin-bottom: 10px;
}
.email-input {
  background-color: #ffffff;
  margin-left: 80px;
  margin-right: 0px;
  padding-right: 0px;
  height: 41px;
  width: 23vw;
  border-bottom-left-radius: 5px;
  border-top-left-radius: 5px;
  padding-left: 15px;
}
.button {
  background-color: #428bca;
  padding-block: 10px;
  padding-inline: 20px;
  font-size: 16px;
  border-bottom-right-radius: 5px;
  border-top-right-radius: 5px;
  font-family: 'Open Sans', sans-serif;
  font-weight: 400;
  color: #ffffff;
  height: 41px;
}
@media screen and (max-width: 1153px) {
  .component-box {
    flex-direction: column;
  }
  .email-input {
    margin-left: 20px;
  }
}
@media screen and (max-width: 800px) {
  .email-input {
    width: 170px;
  }
}
</style>
