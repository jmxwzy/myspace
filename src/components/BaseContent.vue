<template>
  <div class="home">
    <div class="container">
      <div class="card">
        <div class="card-body">
          <!-- 存放父组件传过来的children -->
          <slot></slot>
        </div>
      </div>
    </div>
  </div>
</template>
  
<script>
export default {
  name: "BaseContent",
};
</script>
  
<style scoped>
.container {
  margin-top: 20px;
}
</style>