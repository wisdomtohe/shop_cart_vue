<template>
    <div class="card my-5">
        <div class="card-body">
            <h5 class="text-center card-title">{{product.title}}</h5>
            <p class="text-center text-muted card-text display-4">{{Number(product.price).toFixed()}}$</p>
            <button :disabled="estEnPanier" @click="$emit('ajouter_au_pannier', product)" class="btn btn-primary form-control">
                {{estEnPanier? 'Ajouté au panier' : 'Ajouter au panier'}}
            </button>
        </div>
    </div>
</template>

<script>
export default {
    props:['product','estEnPanier']
}
</script>