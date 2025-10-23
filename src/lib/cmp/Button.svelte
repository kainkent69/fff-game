<script lang="ts">
  export let active = false;
  export let secondary = false;
  export let disabled = false;
  export let className = ""; // optional extra classes
  export let type = "button";

  // Choose button styles based on props
  $: base =
    "px-4 py-2 rounded-lg font-semibold transition-all duration-150 focus:outline-none focus:ring-2 focus:ring-offset-2";

  $: style = secondary
    ? "text-indigo-600 border border-indigo-400 bg-transparent hover:bg-indigo-50"
    : "text-white bg-indigo-600 hover:bg-indigo-500";

  $: activeStyle = active
    ? "ring-2 ring-indigo-400 scale-[0.98]"
    : "hover:opacity-90";

  $: final = `${base} ${style} ${activeStyle} ${disabled ? "opacity-50 cursor-not-allowed min-w-[180px]" : ""} ${className}`;
</script>

<button {type} class={final} {disabled} {...$$restProps as any}>
  <slot />
</button>
