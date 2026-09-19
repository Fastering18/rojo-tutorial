# Rojo Tutorial  

<p align="center">
  <img src="images/jorojo.jpg" alt="Rojo Tutorial Banner" width="900">
</p>

## What is Rojo?  
Rojo is a tool used to synchronize scripts from a **local** folder to **Roblox Studio**.  

## Why bother?  
With Rojo, you can use external code editors like VSCode or Vim, connect to a GitHub repository for collaboration, and get better code assists (autocomplete, GPT, etc.). Any code changes will be automatically updated by Rojo in Studio, and you can click 'Play' to immediately see the effect of your scripts.  

## How?  
It's recommended to follow the steps below to keep your PC clean:  

### 1. Install rokit (toolchain manager):  
https://github.com/rojo-rbx/rokit  
> [!TIP]  
> Read the README and install according to your OS, then restart your PC so `rokit` is added to PATH. You can also add it manually.  

<br />

### 2. Setup Project  
Create a project folder for your game if you haven't already. If it's already on your team's GitHub, you can `git clone` it.  

1. Initialize the project (if it's a new folder):
```sh
rokit init
```  

2. Install rojo:
```sh
rokit add rojo-rbx/rojo
rokit install
```  
This command will add `rojo` to PATH within the project folder environment, then verify:

3. Check rojo:
```sh
rojo --version
```  

4. Setup rojo project:
```sh
rojo init
```  
This will create a `default.project.json` file and a `src/` folder containing template scripts (client, server, shared).

<br />

### 3. Install Rojo Plugin in Roblox Studio  
The plugin is required so Studio can receive changes from the rojo server.

```sh
rojo plugin install
```  

This command will install the plugin to Studio. Check the Plugins tab in Studio to see if Rojo is there.

> [!NOTE]  
> Or install from the browser: https://create.roblox.com/store/asset/13916111004/Rojo 
> After installing, restart Studio if the plugin doesn't show up.

<br />

### 4. Start Rojo  

#### Option A: Using Command (rojo serve)
1. Run the rojo server in your terminal:
```sh
rojo serve
```
2. Open **Roblox Studio** (create a new Place or open an existing one)  
3. In the Studio toolbar, click the **Rojo** plugin > click **Connect**  
4. Rojo will automatically sync all changes from the `src/` folder to Studio **live**  

#### Option B: Using VSCode Extension  
1. Install the **"Rojo - Roblox Studio Sync"** extension from the VSCode marketplace  
![alt text](images/rojoext.png)
2. Open the project folder in VSCode  
3. Click this button:  
![rojo vsc](images/rojovsc.png)

> [!IMPORTANT]  
> Make sure the rojo server **keeps running** during development. If the server stops, Studio will not receive updates from local.

<br />

### 5. How Synchronization Works  
- The folder structure in `src/` is mapped to the Studio tree based on `default.project.json`:  
  | Local Folder | Location in Studio |
  |---|---|
  | `src/server/` | ServerScriptService > Server |
  | `src/client/` | StarterPlayer > StarterPlayerScripts > Client |
  | `src/shared/` | ReplicatedStorage > Shared |


- Click **Play** in Studio to test — no need to copy-paste scripts between local and Studio.   

---  
BTW
As an example, this repo already has rojo initialized with its script folders. If yours looks like this, it's already working and you can proceed to the `serve` step.
