<template>
    <ErrorBox>
      <template #default>

        <div class="not-found-hint">
          <p class="error-code">404</p>
          <h1 class="error-title">Page not found</h1>
          <p>You've landed on a link that doesn't exist.  Try the Search!</p>
        </div>
      </template>
    </ErrorBox>
</template>
<script setup lang="ts">
    import ErrorBox from "vuepress-theme-hope/layouts/NotFound.js";;
        gtag('event', '404_error', {
            'app_name': 'Rundeck_Docs',
            'screen_name': '404 Error'
        });
</script>