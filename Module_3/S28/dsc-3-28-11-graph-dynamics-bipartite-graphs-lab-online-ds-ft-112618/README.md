
# Network Dynamics: Bipartite Graphs - Lab

## Introduction
Let's put our understanding of bipartite graphs to practice. In this lab , we shall look at analyzing bipartite graph of individuals and organizations they belonged to, during the times of American revolution. We shall also look at making a meaningful visualization of the node relationships. 


## Objectives
You will be able to:

- Understand and describe Bipartite graphs in comparison with uni-partite graphs
- Define and analyze bipartite graphs in networkx
- Understand how centrality measures work with bipartite graphs
- Visualize Bipartite graphs


## American Revolution Dataset

This bipartite network contains membership information a number of people in different organisations dating back to the time before the American Revolution. We have this dataset available for you as a csv file `american-revolution.csv`. Load this into a dataframe and inspect the format. Remember we need an edge list to carry on with our analysis. 


The list includes well-known people such as the American activist Paul Revere. Left nodes represent persons and right nodes represent organisations. An edge between a person and an organization shows that the person was a member of the organisation.

## Load Data
- Load the csv file into pandas dataframe and inspect its contents


```python
## Load necessary libraries
import pandas as pd
import networkx as nx
import warnings
warnings.filterwarnings("ignore")
import matplotlib.pyplot as plt

# Read and inspect the dataset

    # Code here
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>StAndrewsLodge</th>
      <th>LoyalNine</th>
      <th>NorthCaucus</th>
      <th>LongRoomClub</th>
      <th>TeaParty</th>
      <th>BostonCommittee</th>
      <th>LondonEnemies</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Adams.John</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Adams.Samuel</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allen.Dr</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Appleton.Nathaniel</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Ash.Gilbert</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



Right so this is not an edge list, rather shows the relationships of individuals with organizations in a matrix form. We need to convert this data into an edge list dataframe. So lets get to it .

## Create edge list
- Convert the individual-club associations into an edge list. You can use the process we saw earlier via graph processing OR use some Python parsing goodness . 


```python
# Create Edge list from CSV file

    # Code here 

# Save edge list as pandas dataframe and view head

    # Code here
```

    [('Adams.John', 'StAndrewsLodge', '0'), ('Adams.John', 'LoyalNine', '0'), ('Adams.John', 'NorthCaucus', '1'), ('Adams.John', 'LongRoomClub', '1'), ('Adams.John', 'TeaParty', '0'), ('Adams.John', 'BostonCommittee', '0'), ('Adams.John', 'LondonEnemies', '0'), ('Adams.Samuel', 'StAndrewsLodge', '0'), ('Adams.Samuel', 'LoyalNine', '0'), ('Adams.Samuel', 'NorthCaucus', '1')]





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>organization</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>Adams.John</td>
      <td>NorthCaucus</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Adams.John</td>
      <td>LongRoomClub</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Adams.Samuel</td>
      <td>NorthCaucus</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Adams.Samuel</td>
      <td>LongRoomClub</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Adams.Samuel</td>
      <td>BostonCommittee</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Adams.Samuel</td>
      <td>LondonEnemies</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Allen.Dr</td>
      <td>NorthCaucus</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Appleton.Nathaniel</td>
      <td>NorthCaucus</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Appleton.Nathaniel</td>
      <td>BostonCommittee</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Ash.Gilbert</td>
      <td>StAndrewsLodge</td>
    </tr>
  </tbody>
</table>
</div>



Great, this makes much more sense. Now we can move further and import this as a networkx graph. 

## Convert edge list to `networkx` graph

-  Read each row as an **edge** with a **source** and a **target**. 
-  Set `name` and `organization` attributes for each edge
-  Visualize the graph


```python
# Create and draw the graph

    # Code here 
```


![png](index_files/index_9_0.png)


We can see the graph is not very revealing at the moment. Adding labels to it would just make it look worse due to occlusion. Also, both individuals and organizations are being shown similarly. How about differentiating clubs from individuals using visual cues like size and color. Let's have a go at it. 

## Visualize the Graph

We would need some list comprehensions and other coding skills to get a meaningful visualization. Let's try to break it down and do it bit by bit. As a first step do the following:
- Make a list of all the organizations from our final edge list dataframe. 


```python
# Make a list of the organizations,

    # Code here
```




    ['NorthCaucus',
     'BostonCommittee',
     'LongRoomClub',
     'LondonEnemies',
     'LoyalNine',
     'StAndrewsLodge',
     'TeaParty']



- Similarly make a list of all unique individuals in the dataframe


```python
# Make a list of the people


    # Code here 
```

    ['Brackett.Jos', 'Flagg.Josiah', 'Chadwell.Mr', 'Burt.Benjamin', 'Howard.Samuel', 'Roylson.Thomas', 'Hunnewell.Jonathan', 'Whitwell.William', 'Fenno.Samuel', 'Collier.Gershom', 'Hancock.John', 'Kimball.Thomas', 'Isaac.Pierce', 'Hammond.Samuel', 'Hooton.John', 'Bradlee.Nathaniel', 'Hopkins.Caleb', 'Bradford.John', 'MacKintosh.Capt', 'Wingfield.William', 'Loring.Matthew', 'Boit.John', 'Edes.Benjamin', 'Brimmer.Herman', 'Prentiss.Henry', 'Spurr.John', 'Stevens.Ebenezer', 'Barber.Nathaniel', 'Williams.Jeremiah', 'Breck.William', 'May.John', 'White.Samuel', 'Merrit.John', 'Ballard.John', 'Moody.Samuel', 'Stoddard.Jonathan', 'Boyer.Peter', 'Moore.Thomas', 'Prince.Job', 'Cazneau.Capt', 'Brown.Hugh', 'Bradlee.David', 'Collins.Ezra', 'Hoskins.William', 'Hitchborn.Nathaniel', 'Pitts.Samuel', 'Whitwell.Samuel', 'Colesworthy.Gilbert', 'Cleverly.Stephen', 'Phillips.William', 'Obear.Israel', 'Austin.Benjamin', 'Waldo.Benjamin', 'Molineux.William', 'Swan.James', 'Tyler.Royall', 'Shed.Joseph', 'Peck.Thomas', 'Adams.John', 'Powell.William', 'Starr.James', 'Winthrop.John', 'Condy.JamesFoster', 'Bolter.Thomas', 'Mason.Jonathan', 'McAlpine.William', 'Jefferds.Unknown', 'Stoddard.Asa', 'Brimmer.Martin', 'Sweetser.John', 'Cooper.Samuel', 'Warren.Joseph', 'Broomfield.Henry', 'Prince.John', 'Phillips.Samuel', 'Kinnison.David', 'Greenough.Newn', 'Davis.Robert', 'Gore.Samuel', 'Webb.Joseph', 'Symmes.John', 'Willis.Nathaniel', 'Cooper.William', 'Hill.Alexander', 'Chrysty.Thomas', 'Revere.Paul', 'Parker.Jonathan', 'Lee.Joseph', 'Dolbear.Edward', 'Urann.Thomas', 'Wheeler.Josiah', 'Pulling.Richard', 'Cheever.Ezekiel', 'Newell.Eliphelet', 'Pearce.Isaac', 'Ash.Gilbert', 'Callendar.Elisha', 'Otis.James', 'Mackay.William', 'Phillips.John', 'Champney.Caleb', 'Field.Joseph', 'Frothingham.Nathaniel', 'Hunt.Abraham', 'Brown.Enoch', 'Bewer.James', 'Inglish.Alexander', 'Trott.George', 'Welles.Henry', 'Eckley.Unknown', 'Appleton.Nathaniel', 'Crafts.Thomas', 'Graham.James', 'Pierpont.Robert', 'Ham.William', 'Eayres.Joseph', 'Matchett.John', 'Hickling.William', 'Campbell.Nicholas', 'Dennie.William', 'Jenkins.John', 'Blake.Increase', 'Pitts.Lendall', 'Machin.Thomas', 'Partridge.Sam', 'Gould.William', 'Milliken.Thomas', 'Slater.Peter', 'Avery.John', 'Wyeth.Joshua', 'Lambert.John', 'Doyle.Peter', 'Baldwin.Cyrus', 'Greenleaf.William', 'Barnard.Samuel', 'Holmes.Nathaniel', 'Burton.Benjamin', 'Palfrey.William', 'Ferrell.Ambrose', 'Pierce.William', 'Ingersoll.Daniel', 'Hewes.George', 'Porter.Thomas', 'Grant.Moses', 'Foster.Bos', 'Greene.Nathaniel', 'Melville.Thomas', 'Randall.John', 'Boynton.Richard', 'Fleet.Thomas', 'Morse.Anthony', 'Dawes.Thomas', 'Lowell.John', 'Payson.Joseph', 'Clarke.Benjamin', 'Simpson.Benjamin', 'Sprague.Samuel', 'Lewis.Phillip', 'Hitchborn.Thomas', 'Eaton.Joseph', 'Ivers.James', 'Foster.Samuel', 'Hoffins.John', 'Davis.Caleb', 'Kent.Benjamin', 'Sessions.Robert', 'Bray.George', 'Cailleteau.Edward', 'Palms.Richard', 'Cochran.John', 'Sharp.Gibbens', 'Lincoln.Amos', 'Quincy.Josiah', 'Russell.John', 'Roby.Joseph', 'Gammell.John', 'Hobbs.Samuel', 'Noyces.Nat', 'Nicholls.Unknown', 'Potter.Edward', 'Emmes.Samuel', 'Proctor.Edward', 'Etheridge.William', 'Smith.John', 'Barrett.Samuel', 'Crane.John', 'Johonnott.Gabriel', 'Deshon.Moses', 'Pitts.John', 'Pulling.John', 'Purkitt.Henry', 'Vernon.Fortesque', 'Mountford.Joseph', 'Bruce.Stephen', 'Jarvis.Edward', 'Allen.Dr', 'Hicks.John', 'Marshall.Thomas', 'Story.Elisha', 'Kerr.Walter', 'Russell.William', 'Tabor.Philip', 'Peck.Samuel', 'Hancock.Eben', 'Williams.Jonathan', 'Wendell.Oliver', 'Church.Benjamin', 'Gray.Wait', 'Marlton.John', 'Sloper.Ambrose', 'Bass.Henry', 'Austin.Samuel', 'Palmer.Joseph', 'Stearns.Phineas', 'Johnston.Eben', 'Chase.Thomas', 'Symmes.Eben', 'Stanbridge.Henry', 'Whitten.John', 'Parkman.Elias', 'Burbeck.Edward', 'Davis.William', 'Greenleaf.Joseph', 'Morton.Perez', 'Brown.John', 'Winslow.John', 'Sigourney.John', 'Spear.Thomas', 'Webster.Thomas', 'Pearce.IsaacJun', 'Adams.Samuel', 'Dexter.Samuel', 'Davis.Edward', 'Bradlee.Josiah', 'Bell.William', 'Burbeck.William', 'Gill.Moses', 'Marett.Phillip', 'Tileston.Thomas', 'Williams.Thomas', 'Chipman.Seth', 'Bradlee.Thomas', 'Hendley.William', 'Jarvis.Charles', 'Marson.John', 'Peters.John', 'MacNeil.Archibald', 'Ruddock.Abiel', 'Hunnewell.Richard', 'Collson.Adam', 'Seward.James', 'Howe.Edward', 'Hunstable.Thomas', 'Young.Thomas']


- Make a list of all the popular people, i.e. with degree > 1 


```python
# Popular ppl with degree > 1


    # Code here 
```

    ['Hancock.John', 'Bradford.John', 'Edes.Benjamin', 'Barber.Nathaniel', 'Molineux.William', 'Swan.James', 'Adams.John', 'Powell.William', 'Winthrop.John', 'Condy.JamesFoster', 'Cooper.Samuel', 'Warren.Joseph', 'Revere.Paul', 'Urann.Thomas', 'Cheever.Ezekiel', 'Otis.James', 'Welles.Henry', 'Appleton.Nathaniel', 'Crafts.Thomas', 'Eayres.Joseph', 'Dennie.William', 'Avery.John', 'Greenleaf.William', 'Grant.Moses', 'Boynton.Richard', 'Davis.Caleb', 'Quincy.Josiah', 'Proctor.Edward', 'Barrett.Samuel', 'Pulling.John', 'Story.Elisha', 'Peck.Samuel', 'Wendell.Oliver', 'Church.Benjamin', 'Bass.Henry', 'Chase.Thomas', 'Parkman.Elias', 'Greenleaf.Joseph', 'Adams.Samuel', 'Ruddock.Abiel', 'Collson.Adam', 'Young.Thomas']


## Calculate Degree
- Calculate the connection `LoyalNine` origanization has.


```python
# Calculate the connection LoyalNine origanization has

    # Code here
```




    10



- Show the degree of all Organizations


```python
# Code here
```




    [59, 21, 17, 62, 10, 53, 97]



## Visualizations
So let's get on with visualizations. It is recommended that you execute one step at a time and inspect the results before moving on. You can change settings for the plot to what suits your eyes better.

Perform following tasks first:
1. Create an empty canvas with figure size=15,15
1. Create a spring layout with our graph `G`.
1.  Go through every organization name in `orgs`, ask the graph how many connections it has. Multiply that by 100 to get the circle size
1.  Use `nx.draw_networkx_nodes()` to draw the organizations with size calculated in the last step. Let's also color these `skyblue` (or one you prefer)
1. Repeat last two steps for individuals in the `ppl` list. In `nx.draw_networkx_nodes()` use color `darkgrey` and node size = 100
1. Repeat the process for third time, with popular people this time. use node size = 300 and color `salmon`. These might overlap a bit so set alpha = 0.5
1. Now draw all the edges with `nx.draw_networkx_edges()`. set edge width = 2 and edge color as `lightgrey`.
1. Create labels for the organizations (i.e. organization names) and draw these with `nx.draw_networkx_labels()`, set font size = 15.
1. Set Plot Title as show.


```python
# 1. Fig size


# 2. Create a layout for our nodes 


# 3. Create org node size as degree*100


# 4. Draw the organizational nodes


# 5. Draw all the people


# 6. Draw popular individuals


# 7. Draw all the edges for the graph


# 8. Draw organization name labels to the graph


# 9. Set a title and show the graph 



```


![png](index_files/index_22_0.png)


## Summary 

IN this lab, we saw how to process, analyze and visualize bipartite graphs. You can try adding more visual cues (i.e. popular people names) etc. to make it more revealing. Also, this looks great as compared to the graphs we plotted in earlier lessons. Visualizing large graphs require interactivity, ability to zoom in and out and filter components to only focus on required information. That is all outside the scope of this section. For now we\ll move on towards looking deeperinto communities and how can we make our analysis more efficient using clustering etc. 
