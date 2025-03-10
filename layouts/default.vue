<template>
  <div>
    <header class="p-3 bg-black">
      <ul class="nav flex gap-5 px-50">
        <li class="nav-item">
          <NuxtLink class="nav-link text-white" to="/"> Главная </NuxtLink>
        </li>
        <li class="nav-item">
          <NuxtLink class="nav-link text-white" to="/contact">
            Контакты
          </NuxtLink>
        </li>
        <li class="nav-item">
          <NuxtLink class="nav-link text-white" to="/users/">
            Пользователи
          </NuxtLink>
        </li>
      </ul>
    </header>

    <div class="py-5 px-50">
      <slot />
    </div>
  </div>
</template>

<style>
header a:not(.router-link-exact-active):hover {
  text-decoration: underline;
}

header a.router-link-exact-active {
  color: #ffb636 !important;
  font-weight: 500;
}
</style>