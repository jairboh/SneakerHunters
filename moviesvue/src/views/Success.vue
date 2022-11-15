<template>
    <div class="page-success">
        <div class="columns is-multiline">
            <div class="column is-12">
                <h1 class="title">Gracias!</h1>

                <p>Tu pedido esta siendo procesado, recibiras un correo con toda la informacion.</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Success',
    mounted() {
        document.title = 'Gracias por el pedido!'
    },
}
</script>