<script lang="ts">
  import copy from 'copy-text-to-clipboard';
  import * as tool from '../lib/tool';
  import Icon from '../component/icon.svelte';

  export let content: any = '';
  export let handler: (content: any) => string = undefined;

  const copyOptions = { target: document.documentElement };
  let showSuc = false;

  const onTapIcon = (e) => {
    let text = content;
    if (tool.isFunction(handler)) {
      text = handler(content) || '';
    } else {
      if (tool.isObject(content) || tool.isArray(content)) {
        text = tool.JSONStringify(content);
      } else {
        text = content;
      }
    }
    copy(text, copyOptions);
    showSuc = true;
    setTimeout(() => {
      showSuc = false;
    }, 600);
  };
</script>

<Icon name="{showSuc ? 'success' : 'copy'}" on:click={onTapIcon}/>
