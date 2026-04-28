<!--
@component
Kicker.svelte — A small uppercase eyebrow label rendered above a headline.

Displays the provided text in the site accent color (CUNY Blue), all-caps,
bold, and with wider letter spacing. Used by DatabaseHeader and ArticleHeader
when an optional kicker string is supplied.

USAGE EXAMPLE:
<Kicker text="Housing Coverage" />
-->
<script>
  let { text = '', href = '' } = $props();
</script>

{#if text}
  <p class="kicker">
    {#if href}
      <a {href}>{text}</a>
    {:else}
      {text}
    {/if}
  </p>
{/if}

<style lang="scss">
  @use '$lib/styles' as *;

  .kicker {
    display: inline-block;
    font-family: var(--font-serif);
    font-size: var(--font-size-xs);
    text-transform: uppercase;
    letter-spacing: var(--letter-spacing-wide);
    color: var(--color-accent);
    margin-bottom: var(--spacing-sm);
    padding: var(--spacing-xs) var(--spacing-sm);
    border: var(--pixel-border);
    background-color: rgba(124, 77, 255, 0.1);
    border-radius: var(--border-radius-sm);
    transition: all 0.2s ease;

    &:hover {
      background-color: rgba(124, 77, 255, 0.2);
      box-shadow: var(--glow-purple);
      transform: scale(1.02);
    }
  }
</style>