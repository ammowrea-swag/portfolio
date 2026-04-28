<!--
@component
Rule.svelte — A horizontal rule for separating content sections.
-->
<hr class="rule" />

<style lang="scss">
  @use '$lib/styles' as *;

  hr {
    border: none;
    height: var(--border-width-divider);
    background: linear-gradient(
      90deg,
      transparent,
      var(--color-accent),
      transparent
    );
    margin: var(--spacing-lg) 0;
    box-shadow: var(--glow-cyan);
  }
</style>
