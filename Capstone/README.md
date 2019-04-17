<!DOCTYPE html>
<html>
<head>
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<style>
	body {font-family: Arial;}

	/* Style the tab */
	.tab {
	  overflow: hidden;
	  border: 1px solid #ccc;
	  background-color: #f1f1f1;
	}

	/* Style the buttons inside the tab */
	.tab button {
	  background-color: inherit;
	  float: left;
	  border: none;
	  outline: none;
	  cursor: pointer;
	  padding: 14px 16px;
	  transition: 0.3s;
	  font-size: 17px;
	}

	/* Change background color of buttons on hover */
	.tab button:hover {
	  background-color: #ddd;
	}

	/* Create an active/current tablink class */
	.tab button.active {
	  background-color: #ccc;
	}

	/* Style the tab content */
	.tabcontent {
	  display: none;
	  padding: 6px 12px;
	  border: 1px solid #ccc;
	  border-top: none;
	}

	table {
	  font-family: arial, sans-serif;
	  border-collapse: collapse;
	  width: 100%;
	}

	td, th {
	  border: 1px solid #dddddd;
	  text-align: left;
	  padding: 8px;
	}

	tr:nth-child(even) {
	  background-color: #dddddd;
	}
	</style>
</head>


<body>
	<h1>What's Seattle Reading?</h1>
	<p>This raw <a href="https://data.seattle.gov/Community/Checkouts-by-Title/tmmm-ytt6"> data set</a> is made available through the Open Data Program by the City of Seattle; it consists of monthly counts by title of checkout for all physical and digital items from 2005 to present from the Seattle Public Library. The set is updated at the beginning of each month, as of March 2019 it contained more than 33 million of entries with 11 columns. Each row is a checkout count with the following information:</p>

<table style="width:80%">
  <tr>
    <th>Column Name</th>
    <th>Description</th> 
    <th>Data Type</th>
  </tr>
  <tr>
    <td>UsageClass</td>
    <td>Denotes if item is “physical” or “digital”</td>
    <td>text</td>
  </tr>
  <tr>
    <td>CheckoutType</td>
    <td>Denotes the vendor tool used to check out the item</td>
    <td>text</td>
  </tr>
  <tr>
    <td>MaterialType</td>
    <td>Describes the type of item checked out (examples: book, song movie, music, magazine)</td>
    <td>text</td>
  </tr>
  <tr>
    <td>CheckoutYear</td>
    <td>The 4-digit year of checkout for this record</td>
    <td>number</td>
  </tr>
    <tr>
    <td>CheckoutMonth</td>
    <td>The month of checkout for this record</td>
    <td>number</td>
  </tr>
    <tr>
    <td>Checkouts</td>
    <td>A count of the number of times the title was checked out within the “Checkout Month”</td>
    <td>number</td>
  </tr>
    <tr>
    <td>Title</td>
    <td>The full title and subtitle of an individual item</td>
    <td>text</td>
  </tr>
    <tr>
    <td>Creator</td>
    <td>The author or entity responsible for authoring the item</td>
    <td>text</td>
  </tr>
    <tr>
    <td>Subjects</td>
    <td>The subject of the item as it appears in the catalog</td>
    <td>text</td>
  </tr>
    <tr>
    <td>Publisher</td>
    <td>The publisher of the title</td>
    <td>text</td>
  </tr>
    <tr>
    <td>PublicationYear</td>
    <td>The year from the catalog record in which the item was published, printed, or copyrighted.</td>
    <td>text</td>
  </tr>
</table>
<br>

<h2>METHODOLOGY</h2>
<h3>OSEMiN</h3>
<p><b>Obtain</b> Gather information, obtain the data. <br> <b>Scrub</b> Clean, reduce noise, remove data that is not needed; check, remove or replace missing or null values, extract columns or format data types. <br> <b>Explore</b> Set up the data, check for multicollinearity, make sure the dataset meets what is necessary for the type of model to apply later on. <br> <b>Model</b> Implement supervised or unsupervised algorithms. <br><b>Interpret</b> Evaluate the results.</p>

<h2>QUESTION</h2>
<p> </p>

<h2>ANALYSIS</h2>
<div class="tab">
  <button class="tablinks" onclick="openCity(event, 'London')">London</button>
  <button class="tablinks" onclick="openCity(event, 'Paris')">Paris</button>
  <button class="tablinks" onclick="openCity(event, 'Tokyo')">Tokyo</button>
</div>

<div id="London" class="tabcontent">
  <div>
    <a href="https://plot.ly/~natyquin/62/?share_key=RAYJgVEQV8ITn73OXp5hcF" target="_blank" title="Checkout Formats" style="display: block; text-align: center;"><img src="https://plot.ly/~natyquin/62.png?share_key=RAYJgVEQV8ITn73OXp5hcF" alt="Checkout Formats" style="max-width: 100%;width: 600px;"  width="600" onerror="this.onerror=null;this.src='https://plot.ly/404.png';" /></a>
    <script data-plotly="natyquin:62" sharekey-plotly="RAYJgVEQV8ITn73OXp5hcF" src="https://plot.ly/embed.js" async></script>
</div>

</div>

<div id="Paris" class="tabcontent">
  <h3>Paris</h3>
  <p>Paris is the capital of France.</p> 
</div>

<div id="Tokyo" class="tabcontent">
  <h3>Tokyo</h3>
  <p>Tokyo is the capital of Japan.</p>
</div>

<script>
function openCity(evt, cityName) {
  var i, tabcontent, tablinks;
  tabcontent = document.getElementsByClassName("tabcontent");
  for (i = 0; i < tabcontent.length; i++) {
    tabcontent[i].style.display = "none";
  }
  tablinks = document.getElementsByClassName("tablinks");
  for (i = 0; i < tablinks.length; i++) {
    tablinks[i].className = tablinks[i].className.replace(" active", "");
  }
  document.getElementById(cityName).style.display = "block";
  evt.currentTarget.className += " active";
}
</script>
   
<h2>RECOMENDATIONS</h2>
<P></P>

<h2>SOURCES</h2>
<ul>
   	<li>https://towardsdatascience.com/understanding-feature-engineering-part-2-categorical-data-f54324193e63</li>
	<li>https://stackoverflow.com/questions/48697770/xgboost-model-consistently-obtaining-100-accuracy</li>
https://machinelearningmastery.com/tactics-to-combat-imbalanced-classes-in-your-machine-learning-dataset/
https://machinelearningmastery.com/classification-accuracy-is-not-enough-more-performance-measures-you-can-use/
https://stats.stackexchange.com/questions/369428/deciding-between-get-dummies-and-labelencoder-for-categorical-variables-in-a-lin
https://discuss.analyticsvidhya.com/t/label-encoding-vs-one-hot-encoding-in-machine-learning-model/7411
https://www.analyticsvidhya.com/blog/2016/03/complete-guide-parameter-tuning-xgboost-with-codes-python/
https://stackoverflow.com/questions/22137723/convert-number-strings-with-commas-in-pandas-dataframe-to-float
https://realpython.com/python-data-cleaning-numpy-pandas/
Andreas C. Müller & Sarah Guido. Introduction to Machine learning with Python. 2017
Jake VanderPlas. Python Data Science Handbook. 2016
</ul>
<P></P>

</body>
</html> 

