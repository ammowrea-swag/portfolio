<!--
@component
Card.svelte — A card container with optional image, link, and footer actions.
-->
<script>
  import { asset } from '$app/paths';

  let { href = '', image = '', imageAlt = '', children, footer } = $props();

  // Resolve local images (those starting with /) using asset()
  // but not external URLs (http://, https://, //, data:)
  const resolvedImage = $derived(
    image && image.startsWith('/') && !image.startsWith('//')
      ? asset(image)
      : image
  );
</script>

{#snippet cardContent()}
  {#if image}
    <div class="card-image">
      <img src={resolvedImage} alt={imageAlt} />
    </div>
  {/if}
  <div class="card-body">
    {@render children()}
  </div>
  {#if footer}
    <div class="card-footer">
      {@render footer()}
    </div>
  {/if}
{/snippet}

{#if href}
  <a {href} class="card card-link">
    {@render cardContent()}
  </a>
{:else}
  <div class="card">
    {@render cardContent()}
  </div>
{/if}

<style lang="scss">
  .card {
    position: relative;
    border: var(--pixel-border);
    border-radius: var(--border-radius-sm);
    background: linear-gradient(
      180deg,
      rgba(20, 15, 29, 0.98) 0%,
      rgba(18, 11, 35, 0.96) 100%
    );
    overflow: hidden;
    display: flex;
    flex-direction: column;
    height: 100%;
    box-shadow:
      var(--glow-purple),
      0 10px 30px var(--color-shadow);
    transition:
      transform 0.2s ease,
      box-shadow 0.2s ease,
      border-color 0.2s ease;

    &::before {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: inherit;
      pointer-events: none;
      box-shadow: inset 0 0 0 1px rgba(0, 229, 255, 0.08);
    }
  }

  .card-link {
    display: flex;
    flex-direction: column;
    height: 100%;
    color: inherit;
    text-decoration: none;

    &:hover {
      transform: translateY(-2px);
      box-shadow:
        var(--glow-cyan),
        0 12px 32px var(--color-shadow);
    }

    &:focus-visible {
      outline: none;
      box-shadow:
        var(--glow-cyan),
        0 0 0 2px rgba(255, 234, 0, 0.5),
        0 12px 32px var(--color-shadow);
    }
  }

  .card-image {
    border-bottom: 1px solid rgba(0, 229, 255, 0.12);

    img {
      display: block;
      width: 100%;
      height: auto;
    }
  }

  .card-body {
    padding: var(--spacing-md, 1rem);
    flex: 1;

    :global(h3) {
      font-size: 1.1rem;
      margin: 0 0 0.5rem;
      line-height: 1.3;
      color: var(--color-clyde, #ffb347);
    }

    :global(p) {
      font-size: 0.9rem;
      margin: 0;
      line-height: 1.5;
      color: var(--color-white, #fff);
    }
  }

  .card-footer {
    border-top: 1px solid rgba(0, 229, 255, 0.12);
    padding: var(--spacing-sm, 0.75rem) var(--spacing-md, 1rem);
    background: rgba(42, 33, 64, 0.7);
    margin-top: auto;
  }
</style>
