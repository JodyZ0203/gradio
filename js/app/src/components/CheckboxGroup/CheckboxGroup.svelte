<script lang="ts">
	import { CheckboxGroup } from "@gradio/form";
	import { Block } from "@gradio/atoms";
	import StatusTracker from "../StatusTracker/StatusTracker.svelte";
	import type { LoadingStatus } from "../StatusTracker/types";

	export let elem_id: string = "";
	export let elem_classes: Array<string> = [];
	export let visible: boolean = true;
	export let value: Array<string> = [];
	export let value_is_output: boolean = false;
	export let choices: Array<string>;
	export let container: boolean = true;
	export let scale: number | null = null;
	export let min_width: number | undefined = undefined;
	export let mode: "static" | "dynamic";
	export let label: string = "Checkbox Group";
	export let info: string | undefined = undefined;
	export let show_label: boolean;

	export let loading_status: LoadingStatus;
</script>

<Block
	{visible}
	{elem_id}
	{elem_classes}
	type="fieldset"
	{container}
	{scale}
	{min_width}
>
	<StatusTracker {...loading_status} />

	<CheckboxGroup
		bind:value
		bind:value_is_output
		{choices}
		{label}
		{info}
		{show_label}
		on:select
		on:change
		on:input
		disabled={mode === "static"}
	/>
</Block>
