<script>
    import Button from "$lib/components/ui/button/button.svelte";
    import Label from "$lib/components/ui/label/label.svelte";
    import TextInput from "./inputs/TextInput.svelte";

    let { formSchema = $bindable() } = $props();
</script>

<form action="/" method="post" class="space-y-2">
    {#each formSchema as item}
        <!-- content here -->
        {#if item.type == "text"}
            <Label>{item.title}</Label>
            <TextInput attributes={item.attributes} />
            <Button
                onclick={() => {
                    item.attributes.class = "bg-blue-300";
                }}
            >
                HI</Button
            >
        {:else if item.type == "number"}
            <!-- content here -->
        {:else if item.type == "email"}
            <!-- content here -->
        {:else if item.type == "password"}
            <!-- content here -->
        {:else if item.type == "file"}
            <!-- content here -->
        {:else if item.type == "radio"}
            <!-- content here -->
        {:else if item.type == "checkbox"}
            <!-- content here -->
        {:else if item.type == "select"}
            <!-- content here -->
        {:else if item.type == "textarea"}
            <!-- content here -->
        {:else if item.type == "date"}
            <!-- content here -->
        {:else if item.type == "time"}
            <!-- content here -->
        {:else if item.type == "range-slider"}
            <!-- content here -->
        {:else if item.type == "switch"}
            <!-- content here -->
        {:else if item.type == "color-picker"}
            <!-- content here -->
        {:else if item.type === "options"}
            <!-- else content here -->
        {:else}
            <!-- else content here -->
        {/if}
    {/each}
    <Button type="submit">Submit</Button>
</form>
