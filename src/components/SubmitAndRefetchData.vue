<template>
    <div>
        <div>
            <input type="radio" id="male" name="sex" value="male" v-model="selectedSex">
            <label for="male">male</label>
        </div>
        <div>
            <input type="radio" id="female" name="sex" value="female" v-model="selectedSex">
            <label for="female">female</label>
        </div>
    </div>
</template>

<script>

export default {
    data() {
        return {
            selectedSex: null // male or female,
        }
    },

    methods: {
        fetchData() {

        }
    }
}

</script>
