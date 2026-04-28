<!--
@component
Headline.svelte — A large serif h1 headline shared by ArticleHeader and DatabaseHeader.

Displays the provided text as a bold serif heading in the site dark color with
tight line-height. Font size steps up at the tablet breakpoint.

USAGE EXAMPLE:
<Headline text="City Council Approves New Budget" />
-->
<script>
  let {
    text = '', // The headline text to display
  } = $props();
</script>

{#if text}
  <h1 class="headline">{text}</h1>
{/if}

<style lang="scss">
  h1 {
    margin: var(--spacing-md) 0 var(--spacing-lg);
    line-height: var(--leading-heading);
    color: var(--color-yellow);
    display: inline-block;
    transition: transform 0.2s ease, text-shadow 0.2s ease;
    will-change: transform;
    cursor: default;
  
    &:hover {
      animation: bounce 620ms cubic-bezier(.215,.61,.355,1);
      text-shadow: var(--glow-cyan);
    }
  }

  @keyframes bounce {
    0% {
      transform: translateY(0);
    }
    30% {
      transform: translateY(-8px);
    }
    50% {
      transform: translateY(0);
    }
    70% {
      transform: translateY(-4px);
    }
    100% {
      transform: translateY(0);
    }
  }
</style>