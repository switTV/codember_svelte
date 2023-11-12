<script lang="ts">
    import { texto_encriptado2 } from "$lib/context/store";
    import { valor_resultado } from "$lib/context/store";

    
    $: texto_modificado = $texto_encriptado2.split("")
    
    function compilador() {
        debugger
        texto_modificado.forEach(letra => {
            if(letra === "&"){
                
            }
            else if(letra === "#"){
                let valor_sumado = $valor_resultado += 1
                return valor_sumado
            }
            else if(letra === "@"){
                let valor_restado = $valor_resultado -= 1
                return valor_restado
            }
            else if(letra === "*"){
                let valor_multiplicado = $valor_resultado = $valor_resultado * $valor_resultado
                return valor_multiplicado
            }
            else{
                throw new Error("El input presentado contiene letras/simbolos no aptas")
            }
        })
        debugger

    }

</script>

<style>
    
</style>

<!-- markup (zero or more items) goes here -->

<textarea cols="30" rows="10" bind:value={$texto_encriptado2}></textarea>
<button on:click={() => {compilador()}}>revelar</button>
<p>{$valor_resultado}</p>