<template>
    <table class="table">
        <thead>
            <tr>
                <slot name="thead"></slot>
            </tr>
        </thead>
        <tbody>
            <template v-for="(item,index) in paraentList" :key="'item'+index">
                <tr>
                    <slot name="list" :row="item"></slot>
                </tr>
            </template>
            <tr v-if="paraentList.length === 0">
				<td colspan="99">검색결과가 없습니다</td>
			</tr>
        </tbody>
    </table>
</template>

<script>
export default {
    props:{
        parentData:{
            type: String,
            required: false,
            default: ""
        },
        paraentList:{
            type:Array,
            default() {
				return [];
			},
        }
    },
    setup(props){
        return{
            props
        }
    }
}
</script>

<style>
.table{
    margin: 0 auto;
    border: 1px solid #444444;
}
th, td {
    border: 1px solid #444444;
}

</style>