<script lang="ts">
    import Button from "$lib/components/ui/button/button.svelte";
    import Input from "$lib/components/ui/input/input.svelte";
    import Label from "$lib/components/ui/label/label.svelte";
    import FormRenderer from "$lib/form-render/FormRenderer.svelte";
    import Sortable from "sortablejs";
    import { onMount } from "svelte";

    let toolbox: HTMLDivElement | undefined = $state();
    let editor: HTMLDivElement | undefined = $state();
    let sortable: Sortable;

    let abc: any[] = $state([]);
    onMount(() => {
        Sortable.create(toolbox!, {
            animation: 320,
            group: { pull: "clone", name: "shared" },
        });
        sortable = Sortable.create(editor!, {
            animation: 320,
            group: { pull: "clone", name: "shared" },
            onEnd: (ev) => {
                ev.item;
            },
            onAdd(e) {
                abc.push({
                    title: "Last Name",
                    name: "l_name",
                    type: "text",
                    attributes: {
                        required: true,
                        class: "shadow-lg m-2 my-10",
                    },
                    variant: "",
                    style: "",
                });
                e.item.remove();
                // console.log(JSON.parse(e.item.dataset.bulla));
            },
        });
    });
</script>

<div class="flex justify-around">
    <div
        bind:this={toolbox}
        class="h-[90vh] shadow w-[20%] space-y-5 m-2 border-2 rounded-lg"
        contenteditable="false"
    >
        {#each Array(5) as item, idx}
            <!-- content here -->
            <!-- <div
                class="w-[90%] my-2 rounded-2 m-auto p-2 border bg-white shadow"
                data-my={{ name: "", class: "" }}
                data-id={idx}
            >
                Block {idx}
            </div> -->
            <div
                class="space-y"
                data-bulla={`{ name: ${"aradhya"}, tiwari: ${"surname"} }`}
            >
                <div contenteditable="true">Title</div>
                <Input type={"text"} class="cursor-pointer" />
            </div>
        {/each}
        <Button
            type="submit"
            onclick={() => {
                console.log(sortable.toArray());
            }}>GetForm</Button
        >
    </div>
    <div
        bind:this={editor}
        class="h-[90vh] shadow w-[70%] m-2 border-2 rounded-lg"
    >
        <FormRenderer bind:formSchema={abc} />
        <Button
            variant="outline"
            onclick={(e) => {
                abc[1].attributes.class = "bg-red-300";
            }}>Tell</Button
        >
    </div>
</div>
