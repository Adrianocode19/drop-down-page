<template>
  <section>
    <div class="containerText">
      <h2>Make remote work</h2>
      <p class="text">
        Get your team in sync, no matter your location. Streamline processes,
        create team rituals, and watch productivity soar.
      </p>
      <button class="btn">Learn more</button>
    </div>
    <Logos />
  </section>
</template>

<style scoped>
section {
  display: flex;
  padding: 0 15px;
  flex-direction: column;
  align-items: center;
  text-align: center;
  row-gap: 48px;
  column-gap: 24px;
}
.containerText {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 22px;
}

h2 {
  font-size: 36px;
  font-weight: bold;
}

.text {
  font-size: 16px;
  line-height: 26px;
  color: #686868;
}
.btn {
  padding: 16px 22px;
  background-color: #151515;
  border: none;
  border-radius: 10px;
  font-size: 16px;
  font-weight: bold;
  color: #fafafa;
  transition: all 0.3s ease;
}

@media (min-width: 1200px) {
  section {
    width: 540px;
    text-align: start;
    justify-content: space-between;
    gap: 48px;
  }

  .containerText {
    align-items: flex-start;
    gap: 50px;
    padding-top: 80px;
  }

  h2 {
    font-size: 77px;
  }

  .text {
    font-size: 18px;
  }

  .btn:hover {
    background-color: transparent;
    color: #151515;
    border: 1px solid #151515;
  }
}
</style>
