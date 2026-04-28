<!--
@component
Tag.svelte — A small pill label for skills, categories, or linked resources.
-->
<script>
  let { text = '', href = '' } = $props();
</script>

{#if href}
  <a class="tag" {href} target="_blank" rel="noopener noreferrer"
    >{text}<svg class="arrow" viewBox="0 0 12 12" aria-hidden="true"
      ><path
        d="M2 10L10 2M10 2H4M10 2v6"
        fill="none"
        stroke="currentColor"
        stroke-width="1.75"
        stroke-linecap="round"
        stroke-linejoin="round"
      /></svg
    ></a
  >
{:else}
  <span class="tag">{text}</span>
{/if}

<style lang="scss">
  .tag {
    display: inline-flex;
    align-items: center;
    gap: 0.1em;
    padding: var(--spacing-xs) var(--spacing-sm);
    background: linear-gradient(
      180deg,
      rgba(42, 33, 64, 0.95) 0%,
      rgba(20, 15, 29, 0.98) 100%
    );
    color: var(--color-text);
    font-family: var(--font-sans);
    font-size: var(--font-size-sm);
    line-height: var(--leading-normal);
    text-decoration: none;
    color: var(--color-inky);
    border: 1px solid rgba(0, 229, 255, 0.22);
    border-radius: var(--border-radius-sm);
    box-shadow: var(--glow-cyan);
    text-shadow: 0 0 8px rgba(0, 255, 255, 0.35);
    transition:
      transform 0.2s ease,
      box-shadow 0.2s ease,
      background 0.2s ease,
      opacity 0.2s ease;
  }

  .arrow {
    width: 0.75em;
    height: 0.75em;
    margin-left: 0.4em;
    vertical-align: baseline;
  }

  a.tag:hover {
    background: linear-gradient(
      180deg,
      rgba(124, 77, 255, 0.2) 0%,
      rgba(42, 33, 64, 1) 100%
    );
    box-shadow:
      var(--glow-purple),
      0 0 0 1px rgba(124, 77, 255, 0.35) inset;
    transform: translateY(-1px);
  }
</style>
