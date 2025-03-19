# Ex.No: 4  Create a player Movement Script in unity 
### DATE: 19.12.2025                                                                           
### REGISTER NUMBER : 212224230181
### AIM: 
To write a program to create a player movement in unity.
### Algorithm:
1. Create a New Unity Project by Open the  Unity Hub and create a new 3D Project,Name the project (e.g., PlayerMovement).
2. Create the Moving Object
   In the Hierarchy, right-click → 3D Object → Capsule (or Sphere).
   Rename it to Player 
4. Adding the Player Movement Behavior Script
   Create the Script-In the Project Window, go to the Assets folder.
   Right-click → Create → C# Script.
5. Write a script for player behavior and save it
6. Attach the Script
   Select player in the Hierarchy - Drag & Drop the playerBehavior script onto the Inspector Panel.
7. Run the game 
8. Stop the program
    
### Program:
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player_movement : MonoBehaviour
{
    // Start is called before the first frame update
    public float speed;
    void Start()
    {
    }

    // Update is called once per frame
    void Update()
    {
       float xdir = Input.GetAxis("Horizontal") * speed;
      float zdir = Input.GetAxis("Vertical") * speed;
      transform.position+=new Vector3(xdir, zdir); 
    }
}

```
### Output:

![Screenshot 2025-03-19 152044](https://github.com/user-attachments/assets/84de6535-c52e-45f1-a715-1582c85336d9)

![Screenshot 2025-03-19 152107](https://github.com/user-attachments/assets/f6d7cbd1-699a-4c9c-8189-b635eececeb2)

![Screenshot 2025-03-19 152151](https://github.com/user-attachments/assets/5f8d31cf-fd69-4bcd-98c1-dca7aa5d7c17)



### Result:
Thus the simple movement behavior was implemented successfully.
