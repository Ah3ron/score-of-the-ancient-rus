<script>
  import "../app.postcss";
  import { AppShell, AppBar } from "@skeletonlabs/skeleton";
</script>

<!-- App Shell -->
<AppShell>
  <svelte:fragment slot="header">
    <!-- App Bar -->
    <AppBar>
      <svelte:fragment slot="lead">
        <strong class="text-xl uppercase"
          >Ah<span class="text-error-500">3</span>ron</strong
        >
      </svelte:fragment>
      <svelte:fragment slot="trail">
        <a
          class="btn btn-sm variant-ghost-surface"
          href="https://www.youtube.com/watch?v=p8z6UeHYQrA"
          target="_blank"
          rel="noreferrer"
        >
          Docs
        </a>
        <a
          class="btn btn-sm variant-ghost-surface"
          href="https://github.com/ah3ron"
          target="_blank"
          rel="noreferrer"
        >
          GitHub
        </a>
      </svelte:fragment>
    </AppBar>
  </svelte:fragment>
  <!-- Page Route Content -->
  <slot />
</AppShell>
