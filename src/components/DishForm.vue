<template>
    <div class="dish">
        <form class="ui form">
            <div class="fields">
                <div class="six wide field">
                    <label>Image</label>
                    <input type="text" name="image" placeholder="Plate Image" @change="handleChange" :value="form.image" />
                </div>

                <div class="four wide field">
                    <label>Plate Name</label>
                    <input type="text" name="plate" placeholder="Plate Name" @change="handleChange" :value="form.plate" />
                </div>

                <div class="four wide field">
                    <label>Price</label>
                    <input type="number" name="price" placeholder="Price" @change="handleChange" :value="form.price" />
                </div>

                <div class="four wide field">
                    <label>Description</label>
                    <input type="text" name="description" placeholder="Description" @change="handleChange"  :value="form.description" />
                </div>
                <div class="two wide field">
                    <button :class="btnClass" @click="onFormSubmit">{{ btnName }}</button>
                </div>

            </div>
        </form>
    </div>
</template>

<script>
    export default {
    name: 'DishForm',
    data() {
        return {
            btnName: "save",
            btnClass: "ui primary button submit-button"
        }
    },
    props: {
        form: {
            type: Object
        }
    },
    methods: {
        handleChange(event){
            const{ name, value} = event.target;
            let form = this.form;
            form[name] = value;
            this.form = form;
        },
        onFormSubmit(e) {
            e.preventDefault();

            if(this.formValidation()) {
                // window.console.log("ready to submit");
                this.$emit("onFormSubmit", this.form);

                //change the button to save
                this.btnName = "Save";
                this.btnClass = "ui primary button submit-button";

                //clear form fields
                this.clearFormFields();
            }
        },
        formValidation() {
            if(document.getElementsByName('plate')[0].value === ""){
                alert('Enter Plate name');
                return false;
            }
             if(document.getElementsByName('price')[0].value === ""){
                alert('Enter Price plate');
                return false;
            }
             if(document.getElementsByName('description')[0].value === ""){
                alert('Enter Description plate');
                return false;
            }
             if(document.getElementsByName('image')[0].value === ""){
                alert('Enter image');
                return false;
            }
            return true;
        },
        clearFormFields() {
            //clear form data
            this.form.plate = "";
            this.form.price = "";
            this.form.description = "";
            this.form.image = "";
            this.form.isEdit = false;

            //clear form fields
            document.querySelector('.form').reset();
        }
    },
    updated () {
        if(this.form.isEdit) {
            this.btnName = "Update";
            this.btnClass = "ui orange button submit-button";
        }
    }
};

</script>