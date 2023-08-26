# ARENA - LADDERS
Ladders - Contributed by [Cooliokid956](https://github.com/Cooliokid956), to the Arena mod for [sm64ex-coop](https://github.com/djoslin0/sm64ex-coop), latter two by [djoslin0](https://github.com/djoslin0).

# Tutorial
###### Kindly read the tutorial carefully and pay close attention to the formatting, else you will miss certain bits.
## Prerequisites
Ladders are provided by the `arena-ladder.lua` file present in Arena folder (i.e. `sm64ex-coop/build`**`/us_pc/mods/arena`**).

| Model ID | Behaviour Name |
| ----- | ----- |
| `MODEL_NONE` | `id_bhvArenaLadder` |

This tutorial assumes that you:
1. Are Familiar with [Blender](https://www.blender.org/).
2. Have installed and are familiar with the [Fast64](https://github.com/Fast-64/fast64) plugin.
3. Have a Fast64 level already setup.

## Adding Ladders To Your Level
1. Add an _Empty_ in Blender, set its __Object Type__ to `Object`. (Move this _Empty_ to the _Area_ empty.)
2. Set __Model__ to _Custom_.
3. Set __Model ID__ as `MODEL_NONE`.
4. Also set its __Behaviour__ to _`Custom`_ and __Behaviour Name__ to `id_bhvArenaLadder`.
   
   ![Example](https://github.com/Cooliokid956/HL-Addon/assets/72434298/0198304e-f632-4923-b9a6-50bb28867c54)

- ## Positioning The Ladder
5. Toggle _Snap_ mode in Blender, and set _Snapping_ to _Edge Centre_.
   ![Snapping](https://github.com/Cooliokid956/HL-Addon/assets/72434298/04877df4-9dc3-48e1-9bf8-72453161b007)
   
6. Move the _Empty_ towards the centre of the ladder's frontal base till it snaps, rotate the _Empty_ if your ladder is facing another direction. (It is good to use Cone Empty as Rovert says.)
   
   ![Movement](https://github.com/Cooliokid956/HL-Addon/assets/72434298/955ebd74-a6ad-4fa7-bae9-4728658d0e99)

7. After it has been placed at the edge centre, set _Transformation Orientation_ to **Local**.

   ![image](https://github.com/Cooliokid956/HL-Addon/assets/72434298/d20f33d6-f2fe-45aa-bcf5-a4e6fa7b9d02)

8. Move the ladder _Empty_ a little forward in the Y axis. In the drop-down box, set `Y = 0.3`, and set `Z = 0.5` (these values are strictly positive). All as shown in the GIF below.
   
   ![Finer adjustments for better gameplay](https://github.com/Cooliokid956/HL-Addon/assets/72434298/fbf1a5f7-6209-4c0a-80f0-e8f723ea52c5)
   
## Determining The Height
### Obtaining Values
To determine how high the ladder would allow Mario to climb, we need to calculate the difference between the top and the bottom vertices of the ladder and convert them to Super Mario 64 Units. Following are the steps to obtain the coordinate values:

9. Press N -> _Item_ tab -> Drop-down _Transform_, and select _Global_ coordinates.
10. Value 1: Select your ladder mesh object and enter _Edit Mode_, then select the bottom most vertex of the ladder. Copy this Z coordinate to Notepad, we'll call it _Z₁_.
    
    ![Base coordinate](https://github.com/Cooliokid956/HL-Addon/assets/72434298/f87e9707-2aad-4b10-8a2e-881535b7fcfa)
    
11. Value 2: Select the top most vertex of the ladder. Copy the Z coordinate to Notepad as well, this will be _Z₂_.
    
    ![Top coordinate](https://github.com/Cooliokid956/HL-Addon/assets/72434298/ed52d57f-ae6e-4f78-8de2-436aa55a27ce)

### Calculations
To get the height of the ladder in terms of Super Mario 64 Units, subtract _Z₁_ from _Z₂_ and multiply the final value by 100 to convert it to SM64 Units. And for better mechanics subtract it by 70 SM64 Units.
###### Please use a calculator and substitute appropriate values.
   Formula: `Height = (Z₂ - Z₁) * 100 - 70`
   
   In __my__ case:
   ```
   Z₂ = 11.0592 M
   Z₁ =  5.5296 M
            Height = (   Z₂   -   Z₁  ) * 100 - 70
                   = (11.0592 - 5.5296) * 100 - 70
                   =   5.5296 * 100 - 70
                   =   552.96 - 70
                   =   482.96 Units
```
Now round this value to the closest Whole Number value. **E.g.** `482.96` -> `483` (I.e. no decimal places.)

## Setting The Height
12. Select the Ladder _Empty_.
13. Go to _Object Properties_ tab.
14. Uncheck _Use Individual Behavior Params_.
15. Input the value which you have calculated earlier into the textbox.
    
    ![image](https://github.com/Cooliokid956/HL-Addon/assets/72434298/19689bf6-bda5-47ac-a4c1-68da23e54c92)

## Conclusion
TL;DR
- Add an _Empty_, set it to _Object_.
- Model ID: `MODEL_NONE` :: Behaviour ID: `id_bhvArenaLadder`
- Move _Empty_ to 'ladder's frontal base centre' by `Edge Centre` snapping.
- Set _Transformation Orientation_ to `Local`.
- Move _Empty_ `0.3` in Y-Axis and `0.5` in Z-Axis, relative to current position.
- Subtract Global Coordinates of ladder's top and bottom vertices for height.
- Convert to SM64 Units by multiplying 100.
- Subtract by 70 for fine tuning.
- Uncheck Individual Behaviour Param -> Input the Height in box.

If you have followed the text properly, you have successfully added the ladders to your level.

Congratulations!

For any queries, curiosities, questions, contact `cooliokid956` or `tobbler_` on Discord.
