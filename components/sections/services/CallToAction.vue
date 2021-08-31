<template>
  <div>
    <div class="wrapper-box">
      <div class="info-box">
        <h3 class="title-text">
          Call To Action
        </h3>
        <p class="description-text text-center">
          Duis aute irure dolor in reprehenderit in voluptate velit esse cillum
          dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
          proident, sunt in culpa qui officia deserunt mollit anim id est
          laborum.
        </p>
        <button class="button">Call To Action</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
.wrapper-box {
  background-attachment: fixed;
  background-position: 0px 70%;
  height: 400px;
  background-image: linear-gradient(
      rgba(0.75, 0.75, 0.75, 0.75),
      rgba(0.75, 0.75, 0.75, 0.75)
    ),
    url('../../../static/imagens/cta-bg.jpg');
}
.info-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 400px;
}
.title-text {
  color: #ffffff;
  font-family: 'Raleway', sans-serif;
  font-size: 28px;
  font-weight: 600;
  margin-bottom: 20px;
}
.description-text {
  color: #ffffff;
  font-family: 'Open Sans', sans-serif;
  font-size: 15px;
  padding-inline: 360px;
  margin-bottom: 20px;
}
.button {
  background-color: #428bca;
  color: #ffffff;
  padding-block: 11px;
  padding-inline: 40px;
  margin-top: 15px;
  font-size: 16px;
  border-radius: 5px;
  margin-top: 10px;
  font-family: 'Raleway', sans-serif;
  font-weight: 600;
}
@media screen and (max-width: 1300px) {
  .description-text {
    padding-inline: 50px;
  }
}
</style>
