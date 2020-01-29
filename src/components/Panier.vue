<template>
    <div>
        <ul class="list-group">
        <li class="list-group-item" v-for="element in elements" :key="element.id">
            {{element.title}} {{element.price}}eco
            <button @click="$emit('enlever', element)" class="badge badge-danger float-right">Enlever</button>
        </li>
    </ul>
    <div class="card p-3 my-5">
        <h4 class="text-center">{{total}} eco</h4>
    </div>
    <button :disabled="elements.length ===0" @click="$emit('pay')" class="btn btn-info form-control">Proceder a l'achat</button>
    </div>
</template>

<script>
export default {
    props:['elements'],
    computed:{
        total(){
            return this.elements.reduce((acc, element)=> acc+Number(element.price), 0)
        }
    }
}
</script>