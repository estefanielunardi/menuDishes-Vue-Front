<template>
    <tr>
        <td>{{ dish.id }}</td>
        <td>{{ dish.image }}</td>
        <td>{{ dish.plate }}</td>
        <td>{{ dish.price }}</td>
        <td>{{ dish.description }}</td>
        <td>
            <button class="mini ui blue button" @click="onEdit">Edit</button>
            <button class="mini ui red button" @click="onDelete">Delete</button>
        </td>
    </tr>
</template>

<script>
export default {
    name: 'Dish',
    props: {
        dish: {
            type: Object
        }
    },
    methods: {
        onDelete() {
            // console.log("Dish Delete" + this.dish.id);
            this.$emit("onDelete" , this.dish.id);
        },
        onEdit() {
            // console.log("Dish Edited" + this.dish.id);
            this.$emit("onEdit" , this.dish);
        }
    }
};
</script>

<style scoped>
</style>