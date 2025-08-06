<script>
    import Input from "$lib/components/ui/input/input.svelte";
    let { attributes } = $props();
</script>

<Input type="text" {...attributes} required={attributes.required} />
