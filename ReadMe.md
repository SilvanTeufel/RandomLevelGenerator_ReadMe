# TopDownRTSCamLib - Readme - 2022

Copyright 2022 Silvan Teufel / Teufel-Engineering.com All Rights Reserved.
This LevelGenerator creaters Actors with StaticMeshes and puts them in a Level on a Random Location.

## Steps to Create a Level with a DataTable

1. Create a Blueprint out of the Classes Component and ComponentGeneratorGameMode
  (In Example they are called BP_Component and BP_GeneratorGameMode)
  
2. Create a DataTable and choose ComponentData as Table Template.
  (you can finde my table in All\Engine\Plugins\RandomLevelGenerator\Content\RandomLevelGenerator\Blueprints\Actors\DT_ComponentData)
  
3. Choose the Table in your BP_Component

4. Choose your ComponentClass (BP_Component) in yoour BP_GeneratorGameMode

5. Fill the Table (for Example DT_ComponentData)

6. Choose the GameMode (for Example BP_GeneratorGameMode) in the LevelEditor and Start the Level

## DataTable

There is a DataTable where you can change:

class UStaticMesh* Mesh;  // Change the Mesh of the Actor

FString Name; // Create a Name 

FVector Scale; // Scale the Mesh

FVector RandomRangeMinMultiplier; // X, Y, Z Min Range till the next Actor will Spawn

FVector RandomRangeMaxMultiplier; // X, Y, Z Max Range till the next Actor will Spawn

int Frequency; // How often should the Object Spawn

FVector AbsoluteOffset; // Offset in any direction

UMaterial* Material; // Choose the Material

bool IsMoving; // Should Actor Move? Yes  -> True

FVector MovementSpeed; // Speed in every direction is chooseable

float MovementRange; // Which Distance to move (after reaching the Object moves back)

## Download the Plugin

If you have downloaded the plugin it can be found in your Unreal Engine folder:
C:\Program Files\Epic Games\UE_5.0\Engine\Plugins\RandomLevelGenerator (for example)
If you can find this folder in your enginge plugins folder the download was successful.
If the plugin is in another folder, you should copy it here.

## Install the Plugin

Open Unreal Editor. Click Edit -> Plugins to open the plugin window.
Search for RandomLevelGenerator and put a check mark at it.

## Test Example Map

Open Unreal Editor. Open folder (In Unreal Editor folder tab):
All\Engine\Plugins\RandomLevelGenerator\Content\RandomLevelGenerator\Level\

## Example Blueprints

Your can find example Blueprints in the Unreal Editor as well:
All\Engine\Plugins\RandomLevelGenerator\Content\RandomLevelGenerator\Blueprints

This Blueprints use the Parent Classes from RandomLevelGenerator Plugin, which you can use for your Blueprints as well.

## Parent Classes

If RandomLevelGenerator is installed the Classes can be used as Parent Class in Blueprint, so all functions from this Class are available.
Just use one of the following Classes as Parent Class and or just choose them in your GameMode Blueprint. Category = TopDownRTSCamLib

Parentclasses are:

- Component
- ComponentGeneratorGameMode


