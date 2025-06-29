<template>
  <header>
    <nav class="navClosed" :class="isMenuOpen ? 'navOpen' : ''">
      <h1 class="title">snap</h1>

      <div :class="['navTopics', { 'navTopics--active': isMenuOpen }]">
        <section class="container containerDropDown">
          <ContainerShow
            :title="'Features'"
            :isOpen="isDropDownFeaturesOpen"
            @toggle="toggleDropDownFeatures"
          />
          <transition name="fade-slide">
            <ul class="list listFeatures" v-show="isDropDownFeaturesOpen">
              <li class="topics">
                <img class="icon" src="../public/assets/icons/list.svg" />Todo
                List
              </li>
              <li class="topics">
                <img
                  class="icon"
                  src="../public/assets/icons/calendar.svg"
                />Calendar
              </li>
              <li class="topics">
                <img
                  class="icon bell"
                  src="../public/assets/icons/bell.svg"
                />Reminders
              </li>
              <li class="topics">
                <img
                  class="icon"
                  src="../public/assets/icons/clock.svg"
                />Planning
              </li>
            </ul>
          </transition>

          <ContainerShow
            :title="'Company'"
            :isOpen="isDropDownCompanyOpen"
            @toggle="toggleDropDownCompany"
          />
          <transition name="fade-slide">
            <ul class="list listCompany" v-show="isDropDownCompanyOpen">
              <li class="topics">History</li>
              <li class="topics">Our Team</li>
              <li class="topics">Blog</li>
            </ul>
          </transition>

          <section class="container containerAbout">
            <a href="#" class="topics link">Careers</a>
            <a href="#" class="topics link">About</a>
          </section>

          <section class="container containerLogin">
            <a class="topics link">Login</a>
            <a class="topics link register">Register</a>
          </section>
        </section>
      </div>

      <img
        v-if="!isMenuOpen"
        @click="toggleMenu"
        class="menuIcon"
        src="../public/assets/icons/menu.svg"
        alt="Menu Hamburger"
      />
      <img
        v-else
        @click="toggleMenu"
        class="menuIcon"
        src="../public/assets/icons/close.svg"
        alt="Close Menu"
      />
    </nav>
  </header>
</template>

<script setup lang="ts">
import { ref, watchEffect } from "vue";

const isMenuOpen = ref(false);
const isDropDownFeaturesOpen = ref(false);
const isDropDownCompanyOpen = ref(false);

watchEffect(() => {
  if (isMenuOpen.value) {
    isDropDownFeaturesOpen.value = false;
    isDropDownCompanyOpen.value = false;
  }
});

const toggleDropDownCompany = () => {
  isDropDownCompanyOpen.value = !isDropDownCompanyOpen.value;
};
const toggleDropDownFeatures = () => {
  isDropDownFeaturesOpen.value = !isDropDownFeaturesOpen.value;
};
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<style scoped>
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}
.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
.fade-slide-enter-to,
.fade-slide-leave-from {
  opacity: 1;
  transform: translateY(0);
}

.navClosed {
  display: flex;
  justify-content: space-between;
  padding: 16px;
  align-items: center;
}

.navOpen::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.75);
  z-index: 1;
}

.title {
  font-size: 35px;
  font-weight: bold;
}

.menuIcon {
  z-index: 1001;
  cursor: pointer;
}

.containerDropDown {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.container {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.link {
  text-decoration: none;
}

.register {
  border: 1px solid #686868;
  padding: 12px 18px;
  border-radius: 15px;
  width: 100%;
  text-align: center;
}

.containerLogin {
  align-items: center;
  margin-top: 22px;
}

.list {
  display: flex;
  flex-direction: column;
  list-style: none;
  padding: 8px 0px 8px 22px;
  gap: 16px;
}

li {
  display: flex;
  align-items: center;
  gap: 14px;
}

.icon {
  width: 20px;
  height: 20px;
}

@media (max-width: 1199px) {
  .navTopics {
    position: fixed;
    top: 0;
    right: 0;
    height: 100vh;
    width: 240px;
    background-color: white;
    opacity: 0;
    visibility: hidden;
    transform: translateX(100%);
    transition: all 0.4s ease;
    flex-direction: column;
    z-index: 1000;
    padding: 2rem;
    display: flex;
  }

  .navTopics--active {
    opacity: 1;
    visibility: visible;
    transform: translateX(0);
  }
}

@media (min-width: 1200px) {
  nav {
    padding: 32px 40px;
    gap: 60px;
  }

  .containerDropDown {
    flex-direction: row;
    gap: 40px;
  }

  .navTopics {
    width: 100%;
  }

  .container {
    width: 100%;
    flex-direction: row;
    align-items: center;
  }

  .menuIcon {
    display: none;
  }

  .containerLogin {
    max-width: 182px;
    margin-top: 0;
  }

  .list {
    position: absolute;
    top: 80px;
    background-color: #ffffff;
    border-radius: 10px;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
    padding: 24px;
  }

  .listFeatures {
    left: 90px;
  }

  .listCompany {
    left: 290px;
  }
}
</style>

<style>
.topics {
  font-size: 16px;
  color: #686868;
  font-weight: normal;
}

@media (min-width: 1200px) {
  .topics:hover {
    color: #151515;
    cursor: pointer;
  }
}
</style>
