# Procedural Generator
___
## Description 
- One of the goals for Omni was to have quasi-procedurally generated levels (maps, worlds, etc.) that the player(s) and NPCs can interact with. Once a 'base' for a level has been established (by generation), manually processing the level to include details and make the level more conrugent in how it flows is essential. 

## Project information

# Procedural Generator
___
## Description 
- One of the goals for Omni was to have quasi-procedurally generated levels (maps, worlds, etc.) that the player(s) and NPCs can interact with. Once a 'base' for a level has been established (by generation), manually processing the level to include details and make the level more conrugent in how it flows is essential. 

## Project information

| Created | Deadline   | Completed                  | Type        | Platform | Dependencies(I)                                          | Dependencies(E)                                                |
| ------------ | ---------- | ------------------------------- | ----------- | -------- | -------------------------------------------------------------- | -------------------------------------------------------------------- |
| Jun-2021    | Mar-2022 | Mar-2022 | Tool | Unity    | Odin Inspector<br>Burst<br>Jobs<br>Addressables<br>2D Tileamps |                                                                      |
|              |            |                                 |             |          |                                                                | UniTask<br> AstarPathfindingProject<br> Debug Drawing Extensions<br> |
| Whinarm's Unity Mesh Simplifier             |            |                                 |             |          |                                                                |                                                                      |
	                                                       |
	

<p class="tab">Created -> June 2021 <br>
	Deadline - > March 2022 <br>
	Completion -> March 2022; sysem extended since completion<br>
Type -> Engine tool <br>
Platform -> Unity <br>
Dependencies, Internal -> Odin Inspector, Burst, Jobs, Addressables, 2D Tilemaps,  <br> 
Dependencies, External -> <a href="UniTask.md" class="internal-link">UniTask</a>, <a href="Astar.md" class="internal-link">AstarPathfindingProject</a>, <a href="DebugDrawExtensions.md" class="internal-link">Debug Drawing Extensions</a>, <a href="whinarm-mesh-simplifier.md" class="internal-link">Whinarm's Unity Mesh Simplifier</a>
<br><br>
The full GitHub repo is available at: GITHUB REPO LINK<br><br>
<b><i>There are a number of dependencies that are required to make this tool work properly. ALL internal & external dependencies listed above are required. I of course will not distribute paid assets through my GitHub repos.</b></i>
</p>

___

## Summary
<div>
<p class="tab">
This tool is based off of <a href="SebastianLague.md" class="internal-link">Sebastian Lague</a>'s <a href="seb-lag-cave-gen.md" class="internal-link">Procedural Cave Generation</a> playlist on his YouTube. 
Information about the overal process of using this tool
</p>
</div>

---

## ProceduralController

![[Pasted image 20220705143116.png]]

### Configuration
- <b><i>Frames To Delay Before Generation</b></i>
	- An integer value for delaying running the generator. I use this to initialize other systems before generating a level. The generator could do without having this feature, but it's there when needed.
- <b><i>Application State</b></i>
	- Internal logic slightly differes between running the generator in the editor vs. an actual build. The generator works in both scenarios.
- <b><i>Runtime State</b></i>
	- Should the generator run at runtime? 
- <b><i>Gizmos</b></i>
	- For drawing tile grids, generated colliders, debugging tiles & grids, and displaying pathfinding nodes, their location, and the centers of each node.

### Flow
> The core approach to running the proccesses in the generator revolves around a concept called "flow". Simply put, it is how each internal solver runs through its logic and in what order. This part of the inspector allows us to select which solver we want for each step in the flow. Required components are:
> 
> 1. Map Solver
> 2. Mesh Solver
> 3. Tile Solver
> 4. Pathfinding Solver
> 5. State Machine
> 
> Events are another dependency  within the generator. This component is straight forward: it serializes UnityEvents to allow of subscribing to internal events per each state in the flow (starting generation, beginning pathfinding, ending pathfinding, etc.) and serializes them. Events can also be subscribed via an exposed API in the ProceduralGenerationEvents class.
> 
> There are three (3) helper classes that are <b><i>not</b></i> <b><i></b></i>required, but add additional funtionality to the generator.
>
> - Procedural Utility Creation
> 	- Contains an API to label tiles, create world text objects, clear tilemaps, and a variety of other functionality
> - Procedural Scaler
> 	- For scaling pathfinding grids & tilemaps
> 	- This does not work as intuitively as I originally intended for it to. It is currently not used within the generator
> - Procedural Controller
> 	- A self-reference to itself for use as a singleton

---

## Resources 
- [[SebastianLague|Sebastian Lague]]
- <a href="https://www.youtube.com/watch?v=v7yyZZjF1z4">Procedural Cave Generation Playlist</a>
- [[Algorithms in Development]]

---

<b>Created:</b> [[Tue Jul 5, 10:44]]
<b><i>Modified:</b></i> [[Tue Jul 5, 15:33]]

#project #procgen #procedural #unity #system #tool












