<script setup lang="ts">
import { fieldConfg } from '../model/field'

</script>

<template>
	<div class="field">
		<a-row :gutter="16" v-for="(row, rowIndex) in fieldConfg.rows" :key="row">
			<a-col v-for="(col, colIndex) in fieldConfg.cols" :key="col">
				<slot :cellCoord="{ rowIndex, colIndex }"></slot>
			</a-col>
		</a-row>
	</div>
</template>

<style scoped lang="scss">
.field
{
	position: relative;
	z-index: 10;

	min-height: 100%;
	height: 100vh;

	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	gap: 16px;
}
</style>