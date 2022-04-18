<script>
	import Selector from './components/Selector.svelte'
    import Select from 'svelte-select';
	import Icon from '@iconify/svelte'
	import { HSplitPane, VSplitPane } from 'svelte-split-pane';
	let blueColor = '#023185';
	let redColor = '#E3303D';
	let files;

	let severityItems = [
		{value: 'Minor', label: 'Minor'},
    	{value: 'Trivial', label: 'Trivial'},
    	{value: 'Major', label: 'Major'}
	];

	let priorityItems = [
		{value: 'Lowest', label: 'Lowest'},
    	{value: 'Low', label: 'Low'},
    	{value: 'Medium', label: 'Medium'},
		{value: 'High', label: 'High'}
	];

</script>

<div class="wrapper">
</div>

<main class="container">

	<HSplitPane leftPaneSize="32%" rightPaneSize="68%" minLeftPaneSize="50px" minRightPaneSize="50px">
	}
		<left slot="left">
			<img src= "https://pbs.twimg.com/media/DN9_SfwV4AATQXt.png" alt="Cemex-Go"
			width="130" height="135">

			<h1 class= "appTitle">Effort Predictor</h1>
			<h3 class= "appSubT">for a given story</h3>

			<p>Results are given in total days of work. <br> <br>

			*If stories are given in a csv file,
			columns should be <br> in order exactly as shown here (Top to bottom).
			</p>
		</left>

		<right slot="right">
			<HSplitPane leftPaneSize="32%" rightPaneSize="68%" minLeftPaneSize="50px" minRightPaneSize="50px">
		 		<left slot="left">
					<section class="story-input">
						<form action=""></form>
							<label for="IssueKey"><span class="labelFont">IssueKey</span></label>
							<input type="text" id="IssueKey" IssueKey="IssueKey" placeholder="Enter IssueKey">
				 
			  		<div class="select-container">
	 
							<label for="Severity"><span class="labelFont">Severity</span></label>
							<Select items = {severityItems}>
							</Select>
			  		</div>
	 
			  		<div class="select-container2">
							<label for="Priority"><span class="labelFont">Priority</span></label>
							<Select items = {priorityItems}>
							</Select>
			  		</div>
	 
							<label for="Summary"><span class="labelFont">Summary</span></label>
							<textarea name="Summary" id="Summary" cols="30" rows="10" placeholder="Enter story summary"></textarea>
	 
							<label for="Description"><span class="labelFont">Description</span></label>
							<textarea name="Description" id="Description" cols="30" rows="10" placeholder="Enter story description"></textarea>
	 
		  
		 			</section>
		 		</left>

				<right slot="right">
					<section class="excel-input">
						<div class="container2">
							<label for="Excel">Multiple stories in a csv file?*</label>
			
							<input type="file" bind:files
									id="file" name="file"
									accept=".csv" class="inputfile" />
							<label for="file" class="inputStyle">
								Select file
							</label>

							{#if files && files[0]}
								<p class ="fileSelected">
							{files[0].name}
								</p>
{							/if}
						</div>

						<input type="submit" class="Predict" value="Predict Effort">
			
					</section>
			
					<section class="file-download">
						<div class="iconContainer">
							<a href="effort_predicted.csv" download>
								<Icon icon="ci:download" color="#0fa958" style="font-size: 77px"/>
							</a>
						
							<a href="effort_predicted.csv" download>
			
						</div>

						<a class="downloadLink" href="effort_predicted.csv" download>
							Download csv file
						</a>

					<input type="reset" class="Clear" value="Enter new story">
					</section>
				</right>
			</HSplitPane>

		</right>

	</HSplitPane>

</main>
  
<div class="triangle"></div>

<style>

	@import url('https://fonts.googleapis.com/css2?family=Raleway:wght@700&display=swap');
	@import url('https://fonts.googleapis.com/css2?family=Raleway&display=swap');



</style>