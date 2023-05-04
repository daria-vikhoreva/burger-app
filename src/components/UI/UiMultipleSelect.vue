<template>
    <div>
        <select name="categories" :size="size" multiple :value="getValue">
            <option value="" @click="clickSelect" disabled selected>{{ getValue }}</option>
            <option 
                v-for="(option, index) in options" 
                :key="index" 
                :value="option.value" 
                @click="clickOption(option)"
            >
                {{ option.name }}
            </option>
            
        </select> 
    </div>
</template>

<script>
    export default {
        name: 'UiMultipleSelect',
        data() {
            return {
                size: 1,
                defaultValue: 'Pick categories',
                selectedCategories: [],
                options: [
                    {name: 'Burger', value: 'burger'},
                    {name: 'Pizza', value: 'pizza'},
                    {name: 'Sandwich', value: 'sandwich'},
                    {name: 'Chicken', value: 'chicken'}
                ]
            }
        },
        methods: {
            clickSelect() {
                this.size = this.size === 1 ? this.options.length : 1;
            },
            clickOption(option) {
                if (this.selectedCategories.includes(option)) {
                    this.selectedCategories = this.selectedCategories.filter(item => item !== option);
                } else {
                    this.selectedCategories.push(option);
                }
            }
        },
        computed: {
            getValue() {
                if (this.selectedCategories.length) {
                    return this.selectedCategories
                        .reduce((acc, curr) => {
                            acc.push(curr.name);
                            return acc;
                        }, [])
                        .toString()
                        .replaceAll(',', ', ');
                } else {
                    return this.defaultValue;
                }
            }
        }
    }
</script>

<style scoped>

select {
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    background-color: transparent;
    border: none;
    margin: 0;
    max-width: 176px;
    width: 100%;
    overflow: hidden;
    font-family: inherit;

    border-radius: 7px;  
    background: linear-gradient(98.81deg, #FFF0F0 -0.82%, #FFDFDF 101.53%);
    mix-blend-mode: soft-light; 
}

select option {
    padding: 10px 12px;
}

</style>