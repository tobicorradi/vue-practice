<template>
  <div class="avatar">
    <img
      class="avatar__image"
      src="https://www.corraditobias.com.ar/img/yo.jpg"
      alt="avatar image"
    />
  </div>
</template>
<script>
export default {
  name: "Avatar",
};
</script>
<style>
.avatar {
  width: 130px;
  height: 130px;
  overflow: hidden;
  display: flex;
  align-items: center;
  border-radius: 100%;
}
.avatar__image {
  width: 100%;
}
</style>
