<script>
    import FormRenderer from "$lib/render/FormRenderer.svelte";
    let formSchema = [
        {
            title: "First Name",
            name: "f_name", // name of the field
            type: "text", // input type,
            attributes: {
                required: true,
            },
            variant: "",
            style: "",
        },
        {
            title: "Last Name",
            name: "l_name",
            type: "text",
            attributes: {
                required: true,
            },
            variant: "",
            style: "",
        },
        {
            title: "E-Mail",
            name: "email",
            type: "email",
            attributes: {
                required: true,
            },
            variant: "",
            style: "",
        },
        {
            title: "Password",
            name: "password",
            type: "password",
            variant: "",
            style: "",
        },
        {
            title: "Upload Resume",
            name: "resume",
            type: "file",
            attributes: {
                required: true,
            },
            variant: "",
            style: "",
        },
    ];
</script>

<div class="w-2/3 m-auto">
    <h1>Form</h1>
    <FormRenderer {formSchema} />
</div>
