<template>
  <div class="slide-panel">
    <div class="logo-wrapper">
      <img :src="logo" alt="logo">
    </div>
    <ul>
      <li :class="{ 'active-item': isActive('/company/create-offer') }">
        <NuxtLink to="/company/create-offer" class="item-field">
          <font-awesome-icon
            class="icon"
            :icon="['fas', 'user-tie']"
            size="xl"
          />
          <span>Crear oferta</span>
        </NuxtLink>
      </li>
      <li :class="{ 'active-item': isActive('/company/load-cvs') }">
        <NuxtLink to="/company/load-cvs" class="item-field">
          <font-awesome-icon
            class="icon"
            :icon="['far', 'file']"
            size="xl"
          />
          <span>Carga CV's</span>
        </NuxtLink>
      </li>
      <li :class="{ 'active-item': isActive('/company/offer-details') }">
        <NuxtLink to="/company/offer-details" class="item-field">
          <font-awesome-icon
            class="icon"
            :icon="['fas', 'chart-column']"
            size="xl"
          />
          <span>Detalle de oferta</span>
        </NuxtLink>
      </li>
      <li :class="{ 'active-item': isActive('/company/offer-list') }">
        <NuxtLink to="/company/offer-list" class="item-field">
          <font-awesome-icon
            class="icon"
            :icon="['fas', 'hippo']"
            size="xl"
          />
          <span>Lista de ofertas</span>
        </NuxtLink>
      </li>
    </ul>
    <div class="bottom-actions">
      <CoreButton
        size="md"
        label="Cerrar sesión"
        :disabled="false"
        :full-width="true"
        @click="onHandleLogout"
      />
    </div>
  </div>
</template>
<script lang="ts" setup>
import { useUserStore } from '~/store/user.store';
import logo from "~/public/images/deepvoice-logo.png";

const userStore = useUserStore()
const route = useRoute()

const onHandleLogout = (): void => {
  userStore.reset();
  navigateTo("/login");
};

const isActive = (path: string): boolean => {
  return route.path === path;
};

</script>
<style lang="scss" scoped>
.slide-panel {
  display: flex;
  flex-direction: column;
  background-color: var(--background-color-secondary);
  font-family: "Avenir", sans-serif;
  height: 100vh;
  padding: 10rem 2rem 2rem 2rem;

  .logo-wrapper {
    text-align: center;
    padding-bottom: 5rem;

    img {
      width: 50%;
      background: white;
      border-radius: 50%;
    }
  }

  ul {
    list-style: none;
    padding: 0;
    font-family: inherit;

    li {
      margin-bottom: 10px;
      padding: 2rem;
      font-family: inherit;

      .item-field {
        display: flex;
        align-items: center;
        gap: 1.5rem;
        font-family: inherit;
        cursor: pointer;
        transition: transform 0.3s ease;

        &:hover {
          transform: scale(1.05);
        }

        span {
          font-size: 1.8rem;
          margin-top: 5px;
          font-family: inherit;
        }
      }

      &.active-item {
        background-color: var(--color-brand);
        border-radius: 1rem;
      }
    }
  }

  .bottom-actions {
    margin-top: auto;
    padding: 2rem;
  }
}
</style>
