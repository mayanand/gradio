<script lang="ts">
	import { Number } from "@gradio/form";
	import { Block } from "@gradio/atoms";
	import StatusTracker from "../StatusTracker/StatusTracker.svelte";
	import type { LoadingStatus } from "../StatusTracker/types";
	import type { Styles } from "@gradio/utils";

	export let label: string = "Number";
	export let elem_id: string = "";
	export let visible: boolean = true;
	export let style: Styles = {};
	export let value: number = 0;
	export let show_label: boolean;

	export let loading_status: LoadingStatus;
	export let mode: "static" | "dynamic";
</script>

<Block
	{visible}
	{elem_id}
	disable={typeof style.container === "boolean" && !style.container}
>
	<StatusTracker {...loading_status} />

	<Number
		bind:value
		{label}
		{show_label}
		disabled={mode === "static"}
		on:change
		on:submit
	/>
</Block>
