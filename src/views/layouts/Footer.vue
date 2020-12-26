<template>
  <footer class="footer">
    <div class="container">
      <div class="copyright">
        &copy; {{ year }} - Powered by
        SMK Telkom Malang
      </div>
    </div>
  </footer>
</template>
<script>
export default {
  props: {
    backgroundColor: String,
    type: String
  },
  data() {
    return {
      year: new Date().getFullYear()
    };
  }
};
</script>
<style></style>
