<template>
    <div class="dish">
        <form class="ui form">
            <div class="fields">
                <div class="six wide field">
                    <label>Image</label>
                    <input type="image" name="image" placeholder="Plate Image" />
                </div>

                <div class="four wide field">
                    <label>Plate Name</label>
                    <input type="text" name="plate" placeholder="Plate Name" />
                </div>

                <div class="four wide field">
                    <label>Price</label>
                    <input type="number" name="price" placeholder="Price"/>
                </div>

                <div class="four wide field">
                    <label>Description</label>
                    <input type="text" name="description" placeholder="Description"/>
                </div>
                <div class="two wide field">
                    <button class="ui primary button submit-button">Save</button>
                </div>

            </div>
        </form>
    </div>
</template>

<script>
    export default {
    name: 'DishForm',
    };

</script>