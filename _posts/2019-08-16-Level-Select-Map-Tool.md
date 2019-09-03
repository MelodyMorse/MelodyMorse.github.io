---
layout: post
title: Level Select Map Tool
categories: Game
img: GameModeMap.PNG
published: true
description: A tool for creating level select maps in Unity 
---

I've been developing a tool for creating level select maps in Unity.  

<iframe width="560" height="315" src="https://www.youtube.com/embed/rXEC9h_hQpM" frameborder="0" allowfullscreen></iframe>

I'm especially proud of the custom Gizmo I designed which visualizes the connections between each map node.
<img src = "{{ site.url }}/images/MapGizmo.PNG">

Here's a little bit about how it works

EasyMaps is a tool to help you create Level Select Maps in Unity. The EasyMaps namespace contains an Enum Direction. The use of this enum will make it easy to add additional directions (for example NorthEast) in future updates.
<pre>
  <code>
    enum Direction {East, South, West, North };
  </code>
</pre>




The namespace also contains struct DirectionInfo
<pre>
  <code>
        public struct DirectionInfo
    {
        public bool hasExit;
        public MapNode neighbor;        
    }
  </code>
</pre>

The map is composed of objects called Map Nodes that have a script with class MapNode attached. Each instance of the MapNode class contains an array of four DirectionInfos, one for each cardinal direction. The user can set hasExit in any of these DirectionInfos to true in the inspector to have the Map Node attempt to find the nearest node in the corresponding direction and make a connection that the player will be able to traverse

<img src= "{{ site.url }}/images/EasyMapsScreenCap1.PNG">

Here is a scene with 2 mapNodes side by side.  The gizmos on the nodes have an X on each of their sides, which indicates that neither of them have any connections yet.

MapNode2 is to the East (right) of MapNode1. So in order to connect them the user only has to set hasExit on MapNode1’s Direction Infos’ Element 0 to true and MapNode1 will connect itself to MapNode2.  Alternatively the user could set hasExit on MapNode2’s Direction Infos’ Element 2 to true

<img src= "{{ site.url }}/images/EasyMapsScreenCap4.PNG">
<img src= "{{ site.url }}/images/EasyMapsScreenCap5.PNG">

Credits: 
The sprites I used are from [kenney.nl](kenny.nl)'s [Map Pack](https://opengameart.org/content/map-pack-180-assets)

