<template>
    <tr >
        <td v-for="header in headers">
            <div>
                {{ cellsDict[header.value].value }}
            </div>
            <div v-if="cellsDict[header.value].error" class="font-weight-bold error--text">

                {{ cellsDict[header.value].error.message }}

            </div>
        </td>
    </tr>
</template>

<script>

    import {mapActions, mapGetters, mapMutations} from "vuex";
    import _ from "lodash";
    import {api, toBase64} from "../../api";

    export default {
        name: "PublisherFileErrorRow",
        props: {
            cellsDict: Object,
            headers: Array,
            label: String,
        },
        data() {
            return {
                dialogIsShowing: false,
                search: "",
            }
        },
        computed: {
            ...mapGetters([
                "publisherId",
            ]),
        },
        methods: {
            ...mapActions([]),
            ...mapMutations([]),
            close() {
                this.dialogIsShowing = false
            },
            open() {
                this.dialogIsShowing = true
            }

        }
    }
</script>

<style scoped>

</style>