<template>
  <div class="logout">
  </div>
</template>

<script>
import axios from "axios";

export default {
  created: function() {
    delete axios.defaults.headers.common["Authorization"];
    localStorage.removeItem("jwt"); // personalize session - remove the new keys
    localStorage.removeItem("user_email"); 
    this.$router.push("/");
  }
};
</script>