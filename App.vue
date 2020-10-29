<template>
  <view class="container">
    <StatusBar color="#FFCE00"/>
  </view>
</template>

<script>
import StatusBar from './components/StatusBar';
export default {
  components: {
    StatusBar
  }
}
</script>

<style>
.container {
  background-color: white;
  flex: 1;
}
</style>
