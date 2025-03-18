<template>
  <NuxtLayout>
    <NuxtLoadingIndicator />
    <NuxtRouteAnnouncer />
    <NuxtErrorBoundary>
      <NuxtPage />
      <template #error="{ error }">
        <main class="main">
          <div class="container">
            <h1 class="title-h1">
              Ошибка
            </h1>
            <p>
              <code>{{ error }}</code>
            </p>
          </div>
        </main>
      </template>
    </NuxtErrorBoundary>
  </NuxtLayout>
</template>

<style lang="scss">
@use "assets/style/utils/reset";
@use "assets/style/utils/fonts";
@use "assets/style/utils/variables";
@use "assets/style/utils/common";

// @use "assets/style/components/container";
// @use "assets/style/components/title";
// @use "assets/style/components/text";
// @use "assets/style/components/section";
</style>
