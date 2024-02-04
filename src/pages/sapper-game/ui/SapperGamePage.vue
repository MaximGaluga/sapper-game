<script setup lang="ts">
import Field from '@/entities/field/ui/Field.vue'
import Cell from '@/entities/cell/ui/Cell.vue'

</script>

<template>
	<a-layout>
		<a-layout-header class="header">
			<a-typography-title class="header__title">Sapper</a-typography-title>
		</a-layout-header>
		<a-watermark content="Designed by Maxim Galuga">
			<a-layout-content>
				<Field>
					<template #default="{ cellCoord }">
						<Cell :cellCoord="cellCoord"></Cell>
					</template>
				</Field>
			</a-layout-content>
		</a-watermark>
	</a-layout>
</template>

<style scoped lang="scss">
.header
{
	margin-bottom: 10px;

	&__title {
		text-align: center;
		color: beige;
		padding-top: 0.15em;
	}
}
</style>

