<template>
  <Navbar>
    <template #endBefore>
      <div class="vp-nav-links">
        <NavbarDropdown :config="links"></NavbarDropdown>
      </div>
    </template>
  </Navbar>

</template>

<script setup lang="ts">
  import Navbar from "vuepress-theme-hope/modules/navbar/components/Navbar.js";
  import NavbarDropdown from "vuepress-theme-hope/modules/navbar/components/NavbarDropdown.js";
  import previousVersions from '../navbar-menus/previous-versions'

  const links = {  text: "Archive", children: previousVersions}
  </script>