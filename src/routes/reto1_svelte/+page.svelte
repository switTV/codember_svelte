<script lang="ts">
    import { texto_encriptado } from "../../lib/context/store";
    import Input from "$lib/components/reto1/input.svelte";
    import TextSquare from "$lib/components/reto1/text_square.svelte";
</script>

<style>
    
</style>

<!-- markup (zero or more items) goes here -->
<Input {texto_encriptado}></Input>
<TextSquare></TextSquare>
