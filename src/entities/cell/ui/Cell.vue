<script setup lang="ts">
import { PropType, ref, computed } from 'vue'
import { CellCoord } from '../model/types'
import { FlagOutlined } from '@ant-design/icons-vue'

const props = defineProps({
	cellCoord: {
		type: Object as PropType<CellCoord>,
		required: true
	}
});

const isCellActive = ref(true);
const isCellFlaged = ref(false);

const openCell = () => {
	isCellActive.value = false;
}

const setFlag = () => {
	isCellFlaged.value = !isCellFlaged.value;
}

</script>

<template>
	<a-card :class="['cell', isCellActive ? 'active' : 'non-active']"
			:hoverable="isCellActive"
			@click="openCell"
			@contextmenu.prevent="setFlag">

		<a-typography-title class="cell__title" :level="2">
			<span class="cell__title--value" v-if="!isCellActive">5</span>
			<FlagOutlined class="cell__title--flag" v-else-if="isCellActive && isCellFlaged"/>
		</a-typography-title>

	</a-card>
</template>

<style scoped lang="scss">
.cell
{
	& :deep(.ant-card-body) {
		width: 80px;
		height: 80px;
		padding: 0;
		border-radius: 8px;
	}

	&.active :deep(.ant-card-body) {
		background-color: gray;
	}

	&.non-active :deep(.ant-card-body) {
		background-color: unset;
		pointer-events: none;
	}

	&__title {
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;

		padding-top: 0;
		margin-bottom: 0;
		line-height: normal;
		
		&--value {
			color: #1bda4f;
		}

		&--flag {
			color: #B00000;
		}
	}
}

@media screen and (max-width: 1200px)
{
	.cell :deep(.ant-card-body)
	{
		width: 50px;
		height: 50px;
		border-radius: 2px;
	}
}
</style>