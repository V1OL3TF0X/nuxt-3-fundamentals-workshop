<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <NuxtLink class="navbar-item" to="/"> My Recs </NuxtLink>

      <a
        role="button"
        class="navbar-burger"
        aria-label="menu"
        aria-expanded="false"
        data-target="navbarBasicExample"
      >
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div id="navbarBasicExample" class="navbar-menu">
      <div class="navbar-end">
        <NuxtLink class="navbar-item" to="/"> Home </NuxtLink>
        <div class="navbar-item has-dropdown is-hoverable">
          <NuxtLink class="navbar-item" to="/display"> Display </NuxtLink>
          <div class="navbar-dropdown">
            <NuxtLink class="navbar-item" to="/display/todos"> Todos </NuxtLink>
            <NuxtLink class="navbar-item" to="/display/photos">
              Photos
            </NuxtLink>
            <a class="navbar-item"> Contact </a>
            <hr class="navbar-divider" />
            <a class="navbar-item"> Report an issue </a>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>
