<script lang="ts">
  import { settings } from '$lib/stores/settings';
  import type Profile from '$lib/entities/Profile';

  export let profile: Profile;
  export let className = '';

  $: isOpenLinkWithApp = $settings.isOpenLinkWithApp;
  $: href = isOpenLinkWithApp
    ? `nostr://${profile.nip19Id()}`
    : `https://snort.social/p/${profile.nip19Id()}`;
</script>

<a {href} target="_blank" rel="noreferrer" class={className}>
  <slot />
</a>
