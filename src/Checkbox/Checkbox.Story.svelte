<script>
  export let story = undefined;

  import Checkbox from "./Checkbox.svelte";
  import CheckboxSkeleton from "./Checkbox.Skeleton.svelte";

  const {
    labelText,
    indeterminate,
    disabled,
    hideLabel,
    wrapperClassName,
  } = $$props;
  const checkboxProps = {
    labelText,
    indeterminate,
    disabled,
    hideLabel,
    wrapperClassName,
  };

  let checked = true;
</script>

{#if story === 'skeleton'}
  <div>
    <CheckboxSkeleton />
  </div>
{:else if story === 'unchecked'}
  <fieldset class="bx--fieldset">
    <legend class="bx--label">Checkbox heading</legend>
    <Checkbox {...checkboxProps} id="checkbox-label-1" />
    <Checkbox {...checkboxProps} id="checkbox-label-2" />
  </fieldset>
{:else}
  <fieldset class="bx--fieldset">
    <legend class="bx--label">Checkbox heading</legend>
    <Checkbox
      {...checkboxProps}
      id="checkbox-label-1"
      bind:checked
      on:check="{({ detail }) => {
        console.log('on:check', detail);
      }}" />
    <Checkbox {...checkboxProps} id="checkbox-label-2" checked />
  </fieldset>
{/if}
