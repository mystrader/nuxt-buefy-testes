<template>
  <div>
    <div>
      <b-navbar>
        <template #brand>
          <b-navbar-item tag="router-link" :to="{ path: '/' }">
            <img
              src="https://github.com/mystrader/nuxt-buefy-testes/blob/main/assets/dhuo_logo.png?raw=true"
              alt="Lightweight UI components for Vue.js based on Bulma"
            />
          </b-navbar-item>
        </template>
        <template #end>
          <b-navbar-item href="#"> Home </b-navbar-item>
          <b-navbar-item href="/steps"> steps </b-navbar-item>
          <select v-model="$colorMode.preference">
            <option value="system">System</option>
            <option value="light">Light</option>
            <option value="dark">Dark</option>
            <option value="sepia">Sepia</option>
          </select>
        </template>
      </b-navbar>

      <section class="main-content columns">
        <aside class="column is-2 section">
          <p class="menu-label is-hidden-touch">General</p>

          <b-dropdown aria-role="list">
            <template #trigger="{ active }">
              <b-button
                label="Click me!"
                type="is-secondary"
                :icon-right="active ? 'menu-up' : 'menu-down'"
              />
            </template>

            <b-dropdown-item aria-role="listitem">Action</b-dropdown-item>
            <b-dropdown-item aria-role="listitem"
              >Another action</b-dropdown-item
            >
            <b-dropdown-item aria-role="listitem"
              >Something else</b-dropdown-item
            >
          </b-dropdown>
        </aside>

        <div class="container column is-10">
          <Nuxt />
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      menus: [
        { icon: 'account-group', text: 'People' },
        { icon: 'shopping-search', text: 'Orders' },
        { icon: 'credit-card-multiple', text: 'Payments' },
        { icon: 'dolly', text: 'Logistics' },
        { icon: 'clock-check', text: 'Jobs' },
        { icon: 'cart-arrow-right', text: 'Cart' },
        { icon: 'settings', text: 'Configuration' },
      ],
    }
  },
}
</script>

<style>
body {
  background-color: #fff;
  color: rgba(0, 0, 0, 0.8);
}
.dark-mode body {
  background-color: #091a28;
  color: #ebf4f1;
}
.sepia-mode body {
  background-color: #f1e7d0;
  color: #433422;
}
</style>
