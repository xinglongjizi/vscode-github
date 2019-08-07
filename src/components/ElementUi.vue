<template>
	<div class="box">
		<div>
			<el-input v-model="data" prefix-icon="el-icon-search" suffix-icon="el-icon-date" size="mini" :disabled="flag" clearable placeholder="请输入内容..."></el-input>
			<el-input v-model="data" size="mini" :disabled="flag" clearable placeholder="请输入内容...">
				<i slot="suffix" class="el-input__icon el-icon-date"></i>
			</el-input>
		</div>
		<div>{{data}}</div>

		<el-input
		type="textarea"
		v-model="data"
		:autosize="{minRows: 2, maxRows: 8}"
		placeholder="请输入内容...">
		</el-input>

		<el-input v-model="data" maxlength="2" show-word-limit></el-input>
		<!-- todo: 带输入建议 -->
		<el-autocomplete
		v-model="autoComplete"
		:fetch-suggestions="querySearch"
		@select="handleSelect"
		:trigger-on-focus="false"
		placeholder="输入域点东西吧...">
		</el-autocomplete>


		<el-input-number
		v-model="number"
		@change="handleChange"
		>
		</el-input-number>

		<!-- 下拉选择组件 -->
		<el-select v-model="selectedValue" clearable placeholder="选择一项吧...">
			<el-option
			v-for="option in options"
			:key="option.value"
			:label="option.label"
			:value="option">
			</el-option>
		</el-select>

		{{selectedValue}}

		<!-- 下拉选择组件之“基础多选” -->
		<el-select v-model="multipleSelected" multiple placeholder="多选...">
			<el-option
			v-for="item in options"
			:key="item.value"
			:value="item.value"
			:label="item.label">
				<span>{{item.label}}</span>
			</el-option>
		</el-select>

		{{multipleSelected}}

		<!-- 可输入过滤的下拉 -->
		<el-select v-model="filterabelSelect" default-first-option :filter-method="filterDropdown" filterable clearable placeholder="可输入...">
			<el-option
			v-for="item in options"
			:key="item.value"
			:value="item.value"
			:label="item.label">
			</el-option>
		</el-select>

		<!-- Cascader 级联选择器 -->









	</div>
</template>

<script>
import { setTimeout } from 'timers';
export default{
	data: function(){
		return {
			data: 'ycsb',
			flag: false,
			autoComplete: '',
			number: 2,
			selectedValue: {value: 300, label: 'c'},
			multipleSelected: [],
			filterabelSelect: '',
			options: [
				{value: 100, label: 'a'},
				{value: 200, label: 'b'},
				{value: 300, label: 'c'},
			],
		};
	},
	methods: {
		filterDropdown: function(inputed){
			this.options = [{value: 2000, label: 'cc'}];
		},
		querySearch: function(inputed, cb){
			var res = [
				{value: 'a'},
				{value: 'b'}
			];
			setTimeout(function(){
				cb(res);
			}, 2000);
		},
		handleSelect: function(item){
			console.log(item);
			console.log( this.autoComplete );
		},
		handleChange: function(){

		},
	},
}
</script>

<style>

</style>
