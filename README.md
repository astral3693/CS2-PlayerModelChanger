# CS2-PlayerModelChanger
A lightweighted counterstrikesharp plugin to change player model.

If you like this plugin, please give a star :)
### This plugin can cause a GSLT ban, please use at your own risk.
[中文教程请点这里](https://github.com/samyycX/CS2-PlayerModelChanger/blob/master/README_CN.md)
- **[Before you use](#before-you-use)**
- [Known issues](#known-issues)
- [Dependencies](#dependencies)
- [Installation Guide](#installation-guide)
- [Commands](#commands)
- [Configuration](#configuration)
- [How to add your own model](#how-to-add-your-own-model)
- [TODOs](#todos)
- [Contribution](#contribution)
## Before you use
1. This plugin is still in development, which means the player's data database structure may be changed **(If changed, the database need to be reseted or be modified by your own)**
## Known issues
1. Windows is unsupported now (due to the ResourcePrecacher plugin)

## Dependencies
1. [ResourcePrecacher](https://github.com/KillStr3aK/ResourcePrecacher)
2. [CS2Fixes](https://github.com/Source2ZE/CS2Fixes)

## Installation Guide
Download the plugin from latest [Release](https://github.com/samyycX/CS2-PlayerModelChanger/releases), then put it into your counterstrikesharp plugin folder.

## Commands
### Server side
- `playermodelchanger_sync_resourceprecacher` Sync with ResourcePrecacher
- `playermodelchanger_enable [true/false]` Enable / Disable the plugin
### Client side
- `!model` show sender the model he is using
- `!model <@random / model name> <all/ct/t>` change sender's model (@random for random model every spawn)
- `!models` show sender all models
- `!resetmodel <all/ct/t>` reset sender's model

## Configuration
When you install the plugin successfully, it will generate `counterstrikesharp/configs/plugins/PlayerModelChanger/PlayerModelChanger.json`.
Config the json like this:
```json
// This configuration was automatically generated by CounterStrikeSharp for plugin 'PlayerModelChanger', at 2024/02/23 11:41:05
{
  "ModelPaths": {
	"model name": "model path",
	"tiara": "characters/tiara/tiara.vmdl", // for example
 },
  "StorageType": "sqlite", // sqlite or mysql
  "MySQL_IP": "",
  "MySQL_Port": "",
  "MySQL_User": "",
  "MySQL_Password": "",
  "MySQL_Database": "",
  "MySQL_Table": "playermodelchanger",
  "ConfigVersion": 1
}
```

## How to add your own model

### Pack your model in a VDF and upload it to steam workshop
**If you already find a workshop item which contains the models you need, you can skip this part**

Requirements:
- Your own model
- Counter-Strike 2 Workshop Tools (which can be installed in `Steam -> cs2 -> properties -> DLC`)

**Step 1.** Open your cs2 directory, find `game/csgo/gameinfo.gi`,
go to the  end of the file, find `AddonConfig -> VpkDirectories`
. Then add the directory you want to put in the vpk like the following example:


*example*:
```json
AddonConfig	
	{
		"VpkDirectories"
		{
			"exclude"       "maps/content_examples"
			"include"       "maps"
			"include"		"characters" // this is the directory you want to add to the vpk
			"include"       "cfg/maps"
			"include"       "materials"
			"include"       "models"
			"include"       "panorama/images/overheadmaps"
			"include"       "panorama/images/map_icons"
			"include"       "particles"
			"include"       "resource/overviews"
			"include"       "scripts/vscripts"
			"include"       "sounds"
			"include"       "soundevents"
			"include"       "lighting/postprocessing"
			"include"       "postprocess"
			"include"       "addoninfo.txt"
		} 
		"AllowAddonDownload" "1"
		"AllowAddonDownloadForDemos" "1"
		"DisableAddonValidationForDemos" "1"
	}
```

**Step 2.** Launch `Counter-Strike 2 Workshop Tools`, then click `Create New Addon`

**Step 3.** Go to folder `./game/csgo_addons/<your addon name>/` and paste your characters folder to here.

**Step 4.** Open `Asset Browser`, then click the `Tools` button on the top-right corner, open `Counter-Strike 2 Workshop Manager`

**Step 5.** Click `New` button in the `Counter-Strike 2 Workshop Manager`, fill in all the information, and publish it.

**Step 6.** After verification, you should be able to use the workshop item.

### Setup CS2Fixes
After you install CS2Fixes plugin, you should have `cs2fixes.cfg` in `./game/csgo/cfg/cs2fixes/` folder.
Modify `cs2f_extra_addon` to your workshop ID.

### Setup ResourcePrecacher
#### Automatically
1. Make sure you install ResourcePrecacher plugin successfully and You have `ResourcePrecacher.json` generated in `counterstrikesharp/configs/plugins/ResourcePrecacher` folder.
2. Type `playermodelchanger_sync_resourceprecacher` in your console. This command will add all models you set in this plugin to ResourcePrecacher config. **(This command will not overwrite old configs. If you want to set again, make sure you delete all old configs in `ResourcePrecacher.json`)**
3. Restart your server.

#### Manually
1. Make sure you install ResourcePrecacher plugin successfully and You have `ResourcePrecacher.json` generated in `counterstrikesharp/configs/plugins/ResourcePrecacher` folder.
2. Add all your model paths into the `ResourcePrecacher.json`
3. Restart your server.

### Config PlayerModelChanger
See the [Configuration](#configuration)

### Fix workshop model hand animations
put your `characters` folder and all folders related to it in **your server's** `./game/csgo/` folder.

## TODOs
1. Translation
2. Beautify command outputs

## Contribution
To build this plugin, run `dotnet build`.

Feel free to create Pull Requests or issues.