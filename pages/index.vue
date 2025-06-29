<template>
  <main>
    <Banner />
    <DescriptionSection />
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  gap: 48px;
}

@media (min-width: 1200px) {
  main {
    max-width: 1300px;
    justify-self: center;
    justify-content: space-between;
    flex-direction: row-reverse;
    padding: 130px;
  }
}
</style>
