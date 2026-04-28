<!--
@component
TagList.svelte — A labeled group of Tag pills.

USAGE EXAMPLE:
<TagList
  label="Skills"
  tags={[
    { text: "Investigative reporting" },
    { text: "Court records analysis" },
    { text: "cuny.edu", href: "https://cuny.edu" },
  ]}
/>
-->
<script>
  import Tag from './Tag.svelte';

  let { label = '', tags = [] } = $props();

  const normalized = $derived(
    tags.map((t) => (typeof t === 'string' ? { text: t } : t))
  );
</script>

<div class="tag-list">
  {#if label}
    <h3 class="tag-list-label">{label}</h3>
  {/if}
  <div class="tag-list-items">
    {#each normalized as tag (tag.text)}
      <Tag text={tag.text} href={tag.href ?? ''} />
    {/each}
  </div>
</div>

<style lang="scss">
  @use '$lib/styles' as *;

  .tag-list {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-xs);
  }

  .tag-list-label {
    margin: 0;
  }

  .tag-list-items {
    display: flex;
    flex-wrap: wrap;
    gap: var(--spacing-sm);
  }
</style>
