
# Graph Theory: Simple and Shortest Paths - Lab

## Introduction
In this lab, we shall work with Florentine families graph.
[Click here to see details on Florantine family dataset](http://www.casos.cs.cmu.edu/computational_tools/datasets/external/padgett/index2.html). This dataset comes bundled with networkx [as shown here](https://networkx.github.io/documentation/stable/reference/generated/networkx.generators.social.florentine_families_graph.html#networkx.generators.social.florentine_families_graph). Visit these links to get some idea about the contents of this dataset. We shall use it as an undirected dataset for this lab and work on identifying paths between different nodes. 
<img src="http://www.promoguidesiena.it/admin/img/022013/1362048286CaterinaDeMediciweddinguffizi5470.jpg" width=300>

## Objectives
You will be able to:
- Load and study Florentine families graph generator in networkx
- Calculate and visualize the different paths between a given set of nodes

### Load and Draw Florentine families graph generator with a Fruchterman Reingold layout

Note: Refer to the documentation for methods to load the required graph and layout. 


```python
# Your code here 
```


![png](index_files/index_3_0.png)


### Calculate shortest path between Medici and Peruzzi families


```python
# Your code here 
```




    ['Medici', 'Barbadori', 'Castellani', 'Peruzzi']



You will see above that the shortest paths may not necessarily be unique i.e. there can be more than one , while counting the number of hops. We can use `all_shortest_paths()` method to find if there are more than one. 

### Calculate all shortest paths between Medici and Peruzzi families


```python
# Your code here 
```




    [['Medici', 'Barbadori', 'Castellani', 'Peruzzi'],
     ['Medici', 'Ridolfi', 'Strozzi', 'Peruzzi']]



### Calculate and draw the shortest path between Lamberteschi and Ridolfi families

- Create a function plot_paths(G, paths) that would take in a graph with calculated path(s)
- Use `fruchterman_reingold_layout()`
- For all paths in `paths`, color the edges and display the graph 
- Print the path in the output 


```python
source = 'Lamberteschi'
target = 'Ridolfi'
```


```python
def plot_paths(G, paths):
    
    # Your code here 
    
    pass
    
print(nx.shortest_path(G, source, target))

plot_paths(G, [nx.shortest_path(G, source, target)])
```

    ['Lamberteschi', 'Guadagni', 'Tornabuoni', 'Ridolfi']



![png](index_files/index_10_1.png)


### Calculate and draw all simple paths between Lamberteschi and Ridolfi families
- Use `nx.all_simple_paths(G, source, target)` to calculate all possible paths between two families and plot them.


```python
# Your code here 
```

    1 ['Lamberteschi', 'Guadagni', 'Tornabuoni', 'Medici', 'Barbadori', 'Castellani', 'Peruzzi', 'Strozzi', 'Ridolfi']
    2 ['Lamberteschi', 'Guadagni', 'Tornabuoni', 'Medici', 'Barbadori', 'Castellani', 'Peruzzi', 'Bischeri', 'Strozzi', 'Ridolfi']
    3 ['Lamberteschi', 'Guadagni', 'Tornabuoni', 'Medici', 'Barbadori', 'Castellani', 'Strozzi', 'Ridolfi']
    4 ['Lamberteschi', 'Guadagni', 'Tornabuoni', 'Medici', 'Ridolfi']
    5 ['Lamberteschi', 'Guadagni', 'Tornabuoni', 'Ridolfi']
    6 ['Lamberteschi', 'Guadagni', 'Albizzi', 'Medici', 'Barbadori', 'Castellani', 'Peruzzi', 'Strozzi', 'Ridolfi']
    7 ['Lamberteschi', 'Guadagni', 'Albizzi', 'Medici', 'Barbadori', 'Castellani', 'Peruzzi', 'Bischeri', 'Strozzi', 'Ridolfi']
    8 ['Lamberteschi', 'Guadagni', 'Albizzi', 'Medici', 'Barbadori', 'Castellani', 'Strozzi', 'Ridolfi']
    9 ['Lamberteschi', 'Guadagni', 'Albizzi', 'Medici', 'Ridolfi']
    10 ['Lamberteschi', 'Guadagni', 'Albizzi', 'Medici', 'Tornabuoni', 'Ridolfi']
    11 ['Lamberteschi', 'Guadagni', 'Bischeri', 'Peruzzi', 'Castellani', 'Strozzi', 'Ridolfi']
    12 ['Lamberteschi', 'Guadagni', 'Bischeri', 'Peruzzi', 'Castellani', 'Barbadori', 'Medici', 'Ridolfi']
    13 ['Lamberteschi', 'Guadagni', 'Bischeri', 'Peruzzi', 'Castellani', 'Barbadori', 'Medici', 'Tornabuoni', 'Ridolfi']
    14 ['Lamberteschi', 'Guadagni', 'Bischeri', 'Peruzzi', 'Strozzi', 'Castellani', 'Barbadori', 'Medici', 'Ridolfi']
    15 ['Lamberteschi', 'Guadagni', 'Bischeri', 'Peruzzi', 'Strozzi', 'Castellani', 'Barbadori', 'Medici', 'Tornabuoni', 'Ridolfi']
    16 ['Lamberteschi', 'Guadagni', 'Bischeri', 'Peruzzi', 'Strozzi', 'Ridolfi']
    17 ['Lamberteschi', 'Guadagni', 'Bischeri', 'Strozzi', 'Castellani', 'Barbadori', 'Medici', 'Ridolfi']
    18 ['Lamberteschi', 'Guadagni', 'Bischeri', 'Strozzi', 'Castellani', 'Barbadori', 'Medici', 'Tornabuoni', 'Ridolfi']
    19 ['Lamberteschi', 'Guadagni', 'Bischeri', 'Strozzi', 'Peruzzi', 'Castellani', 'Barbadori', 'Medici', 'Ridolfi']
    20 ['Lamberteschi', 'Guadagni', 'Bischeri', 'Strozzi', 'Peruzzi', 'Castellani', 'Barbadori', 'Medici', 'Tornabuoni', 'Ridolfi']
    21 ['Lamberteschi', 'Guadagni', 'Bischeri', 'Strozzi', 'Ridolfi']



![png](index_files/index_12_1.png)


## Level Up - Optional 

- Modify the `plot_paths()` to show each path in a different graph, with edge width showing the **distance** between source and target. 

- Prettify the graph entities further in order to make it more presentable

## Summary 

In this lab, we saw how to calculate and visualize paths between a given set of nodes in a graph. The skills learned in these simple exercises can be scaled to deal with much larger networks with possible tens of thousands of nodes (or maybe more) to identify paths between node entities. We mainly looked at calculating the simple distance, but the idea can be applied to directed and weighted networks with same level of ease. 
