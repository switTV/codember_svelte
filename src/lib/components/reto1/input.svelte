<script lang="ts">
    export let texto_encriptado
    import { texto_resuelto } from "$lib/context/store";

    let texto_descifrado = ""

    let palabrasUnicas: string[] = []
    let palabrasRepetidas: string[] = []

    function descifrador(texto:string) {
        let texto_minuscula = texto.toLowerCase().split(" ")

        texto_minuscula.forEach(palabra => {
            if (palabrasUnicas.includes(palabra)) {
                palabrasRepetidas.push(palabra)
            } else {
                palabrasUnicas.push(palabra)
            }
        });
        
        palabrasUnicas.forEach(palabraUnica => {
            let filtraPalabras = palabrasRepetidas.filter(e => palabraUnica === e);
            texto_descifrado += palabraUnica + (filtraPalabras.length + 1);
        });

        construir_resultado()

        function construir_resultado() {
            $texto_resuelto = texto_descifrado
        }
    }
</script>

<style>
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->

<textarea
name="codigo_encriptado" 
placeholder="pon el texto encriptado aqui"
bind:value={$texto_encriptado}
/>
<button on:click={() => {descifrador($texto_encriptado)}}>press</button>