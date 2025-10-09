# Canvas Management



This package contains an easy canvas management system to to make changing the UI easier.



Below are Basic instructions how to use the system.

## Base info

The Canvas will have Canvas Objects (panels).

These panels act as a background for the UI.

[Check the example canvas structure below!](#basic-canvas-structure)

<hr>

### Canvas Object

Add this script to every panel



Each Canvas Object will have a name and a type

There can only be 1 of said type active.

#### Types (More types can be added in Canvas Manager)

* **Base** (Should only be 1, Ingame HUD for example)

* **Overlay** (Goes over the base layer)

* **Modal** (Goes over the Overlay panels)

<hr>

### Canvas Manager

This script needs to be added to an empty gameobject.

#### Canvas Manager has variables

* **Canvas Objects (List)**

    - Add all Canvas Objects to this list

* **Start Enabled (List)**

    - Add all the Canvas Ojects that you want enabled at the Start

* **Start Disabled (List)**

    - Add all the Canvas Ojects that you want Disabled at the Start



* **Lobby Canvas Name (Can be removed)**

    - For multiplayer

    - Used by ReturnToLobby UnityEvent

    - ***IMPORTANT!*** Input the **name** of the Canvas Object given in the **Canvas Object Script**

* **Start Canvas Name**

    - The starting panel

    - ***IMPORTANT!*** Input the **name** of the Canvas Object given in the **Canvas Object Script**

* **Game Canvas Name** 

    - Should be the **Type: Base**

    - Used by ShowGameCanvas UnityEvent

    - ***IMPORTANT!*** Input the **name** of the Canvas Object given in the **Canvas Object Script**

<hr>

### Buttons
There are 3 scripts included for buttons.
All of these should be added to the buttons as components.

* **Change Canvas Button**

    - Calls ShowCanvas UnityEvent

    - Enables said Panel **and** disables all other panels of that **type**!

    - ***IMPORTANT!*** Input the **name** of the Canvas Object given in the **Canvas Object Script** that you want to change to.

* **Close Canvas Button**

    - Calls CloseCanvas UnityEvent

    - Disables all **panels** of **selected type**

    - ***IMPORTANT!*** Input the **type** of Canvas Object you want disabled.

* **Quit Button**

    - Closes Application

<hr>

## Creating New Buttons

You can create new buttons easily by creating a script

Below is a sample script that you can follow:

```c#
[RequireComponent(typeof(Button))]
public class ExampleButton : MonoBehaviour
{
    private void Awake() =>
        GetComponent<Button>().onClick.AddListener(() => 
        {
            /*
            Add your own functionality here

            This example is calling an UnityEvent from a manager

            For example: CanvasManager.ShowCanvas.Invoke(canvasName);
            */

            ExampleManager.ExampleEvent.Invoke();
        });
}
```

<hr>

### Basic canvas structure

* Canvas

    - Panel (**CanvasObject**) (Type: **Base**) (These panels should act as a background for the UI)

        - UI things (Images, buttons, text)

    - Panel2 (**CanvasObject**) (Type: **Overlay / Modal**)

        - UI things (Images, buttons, text)

    - Panel3 (**CanvasObject**) (Type: **Overlay / Modal**)

        - UI things (Images, buttons, text)

