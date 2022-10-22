# TopDownRTSCamLib - Readme - 2022

Copyright 2022 Silvan Teufel / Teufel-Engineering.com All Rights Reserved.

## Download the Plugin

If you have downloaded the plugin it can be found in your Unreal Engine folder:
C:\Program Files\Epic Games\UE_5.0\Engine\Plugins\TopDownRTSCamLib (for example)
If you can find this folder in your enginge plugins folder the download was successful.
If the plugin is in another folder, you should copy it here.

## Install the Plugin

Open Unreal Editor. Click Edit -> Plugins to open the plugin window.
Search for TopDownRTSCamLib and put a check mark at it.

## Import Keyboard Settings

__You can download DefaultInput.ini and InputBackupTopDownRTSCamLib.ini from here from github by clicking on top left Code->Download Zip__

Open Unreal Editor. Go to Edit -> Project Settings -> Input (on left navigation) -> Import.
Choose InputBackupTopDownRTSCamLib.ini from:
C:\Program Files\Epic Games\UE_5.0\Engine\Plugins\TopDownRTSCamLib\TopDownRTSCamLib\Document\Inputs

__or download from github__

Repeat this step with DefaultInput.ini .

If the keybindings are not working you can check the pictures in:
C:\Program Files\Epic Games\UE_5.0\Engine\Plugins\TopDownRTSCamLib\TopDownRTSCamLib\Document\Inputs
and create the keybindings by yourself

## Test Example Map

Open Unreal Editor. Open folder (In Unreal Editor folder tab):
All\Engine\Plugins\TopDownRTSCamLib\Content\Level\

Open Unreal Editor. Open folder (In Unreal Editor folder tab):
All\Engine\Plugins\TopDownRTSCamLib\Content\Level\

## Example Blueprints

Your can find example Blueprints in the Unreal Editor as well:
All\Engine\Plugins\TopDownRTSCamLib\Content\Blueprints

This Blueprints use the Parent Classes from TopDownRTSCamLib Plugin, which you can use for your Blueprints as well.

## Parent Classes

If TopDownRTSCamLib is installed the Classes can be used as Parent Class in Blueprint, so all functions from this Class are available.
Just use one of the following Classes as Parent Class and or just choose them in your GameMode Blueprint. Category = TopDownRTSCamLib

Parentclasses are:

- CameraBase
- CharacterBase
- HUDBase
- ControllerBase
- SelectedCharacterIcon

For CameraBase, if you want only to use the Functions and not run the Code in Tick and BeginPlay (which is automatically setup), just set the Variables to true:

- DisableTick
- DisableBeginPlay

For ControllerBase, if you want to use the Controller, you have to adapt your Settings (Pictures in "Document/Inputs" Folder), or import the DefaultInput.ini and InputBackupTopDownRTSCamLib.ini inside the "Inputs" Folder.
You also have to set Lock Viewport on Mouse as "always".

---

Here is a List of the Classes and there Functions:

### Class - CameraBase

```
void CreateCameraComp();

USceneComponent* RootScene;

USpringArmComponent* SpringArm;

FRotator SpringArmRotator = FRotator(-50, 0, 0);

 UCameraComponent* CameraComp;

 APlayerController* PC;

 void GetViewPortScreenSizes(int x);

 void SpawnControllWidget();

- Functionality is defined by Functionname

FVector GetCameraPanDirection();

void PanMoveCamera(const FVector& PanDirection);

- Scrolling with Screen Edges This is Called in Tick generaly with CamSpeed: PanMoveCamera(GetCameraPanDirection() \* CamSpeed);

float Margin = 15;

int32 ScreenSizeX;

- Screen Edge For Scrolling with Mouse

int32 ScreenSizeY;

- Screen Edge For Scrolling with Mouse

int GetViewPortScreenSizesState = 1;

- Set 2 for System Resolution, Set 1 for Viewport Edges
- The Function Defines ScreenSize X and Y

float CamSpeed = 80;

- Camspeed for Scrolling with Screen Edges

void ZoomIn();

- Functionality is defined by Functionname

void ZoomOut();

- Functionality is defined by Functionname

void ZoomStop();

- Functionality is defined by Functionname

void CamLeft();

- Functionality is defined by Functionname

void CamRight();

- Functionality is defined by Functionname

void CamStop();

- Functionality is defined by Functionname

void CamRotationTick();

- Is Used For Rotation is generaly called in Tick

void JumpCamera(FHitResult Hit);

- Jump Camera to Hit Position

FVector2D GetMousePos2D();

- Functionality is defined by Functionname

void Zoom();

- Functionality is defined by Functionname

void ZoomOutToPosition();

- Functionality is defined by Functionname

void CamMoveAndZoomTick();

- For Cam Movement and Cam Zoom generaly called in Tick

void ZoomInToPosition();

- Sets ZoomCamOutToPosition to true

void LockOnCharacter(ACharacter\* SelectedActor);

- Lock the Camera to an Actor, ZoomCamOutToPosition is checked

float ZoomOutPosition = 20000.f;

- Cameraposition when ZoomOutToPosition() is called.

float ZoomPosition = 1500.f;

- Cameraposition when ZoomInToPosition() is called.

float PitchValue = 0.f;

- Of the Camera

float YawValue = 0.f;

- Of the Camera

float RollValue = 0.f;

- Of the Camera

bool RollCamRight = false;

- Functionality is defined by Functionname

bool RollCamLeft = false;

- Functionality is defined by Functionname

bool ZoomCamOut = false;

- Functionality is defined by Functionname

bool ZoomCamIn = false;

- Functionality is defined by Functionname

bool ZoomCamOutToPosition = false;

- Functionality is defined by Functionname

bool MoveCamForward = false;

- Functionality is defined by Functionname

bool MoveCamBackward = false;

- Functionality is defined by Functionname

bool MoveCamLeft = false;

- Functionality is defined by Functionname

bool MoveCamRight = false;

- Functionality is defined by Functionname

float startTime = 0.f;

- Functionality is defined by Functionname

int CamAngle = 0;

- Should not be changed. Is to keep Track of actual Angle

bool DisableTick = false;

- Disable My Tick Functions of Parent Class, to use my Function in Blueprint

bool DisableBeginPlay = false;

- Disable BeginPlay Functions of Parent Class, to use my Function in Blueprint

class UWidgetComponent\* ControlWidgetComp;

- Keyboard Widget (which is shown by pressing Tab)

FRotator ControlWidgetRotation = FRotator(50, 180, 0);

- Rotation of The Widget

FVector ControlWidgetLocation = FVector(400.f, -350.0f, -250.0f);

- Location of the Widget when shown

FVector ControlWidgetHideLocation = FVector(400.f, -2500.0f, -250.0f);

- Location of the Widget when hidden

void HideControlWidget();

- Functionality is defined by Functionname

void ShowControlWidget();

- Functionality is defined by Functionname

```

---

### Class - HUDBase

```
virtual void DrawHUD();

- Used in Tick() to Draw the Selectionfield and trigger select.

FVector2D InitialPoint;

- Position of mouse on screen when pressed;

FVector2D CurrentPoint;

- Position of mouse on screen while holding;

float RectangleScaleSelectionFactor = 0.9;

- Factor of inner/outer selection field

FVector2D GetMousePos2D();

- Functionality is defined by Functionname

void AimToMouse();

- Actors can be triggert to Look to the Mouse

void MoveActorsThroughWayPoints(TArray <ATopDownExampleCharacter\*> Actors);

- Move Actors through Waypoints

void StartMovingActors(TArray<ATopDownExampleCharacter\*> Actors);

- Start Move Actors.

void setZeroActor(ATopDownExampleCharacter\* Actor);

- Functionality is defined by Functionname

bool bStartSelecting = false;

TArray <ATopDownExampleCharacter\*> FoundActors;
```
---

### Class - ControllerBase

```
void ShiftPressed();

void ShiftReleased();

void LeftClickPressed();

void LeftClickReleased();

void RightClickPressed();

void SpacePressed();

void SpaceReleased();

void QPressed();

void WPressed();

void APressed();

void AReleased();

void JumpCamera();

void StrgPressed();

void StrgReleased();

void ZoomIn();

void ZoomOut();

void ZoomStop();

void CamLeft();

void CamRight();

void ControllDirectionToMouse(ATopDownExampleCharacter\* SelectedActor);

void ToggleLockCameraToCharacter();

void TabPressed();

void TabReleased();

void CameraPawnForward();

void CameraPawnBackward();

void CameraPawnLeft();

void CameraPawnRight();

void CameraPawnForwardR();

void CameraPawnBackwardR();

void CameraPawnLeftR();

void CameraPawnRightR();

bool IsShiftPressed = false;

bool AIsPressed = false;

bool IsStrgPressed = false;

bool IsSpacePressed = false;

bool LockCameraToCharacter = false;

TArray <ATopDownExampleCharacter*> SelectedActors;

TArray <ATopDownExampleCharacter*> MovingActors;
```
