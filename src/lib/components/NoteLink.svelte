<script lang="ts">
  import { settings } from '$lib/stores/settings';
  import type Note from '$lib/entities/Note';

  export let note: Note;
  export let className = '';

  $: isOpenLinkWithApp = $settings.isOpenLinkWithApp;
  $: href = isOpenLinkWithApp
    ? `nostr://${note.nip19Id()}`
    : `https://snort.social/e/${note.nip19Id()}`;
</script>

<a {href} target="_blank" rel="noreferrer" class={className}>
  <slot />
</a>
