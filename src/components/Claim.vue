<template>
  <div class="claimWrapper">
    <h1 class="claim">SPACER</h1>
    <p class="subclaim">Type anything to start</p>
  </div>
</template>

<script>
export default {
  name: 'Claim',
};
</script>

<style lang="scss" scoped>
.claimWrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.claim {
  color: whitesmoke;
  font-size: 50px;
  margin: 0;

  @media (min-width: 768px) {
    font-size: 80px;
  }
}
.subclaim {
  color: white;
  font-size: 15px;

  @media (min-width: 768px) {
    font-size: 17px;
    letter-spacing: 1px;
  }
}
</style>
