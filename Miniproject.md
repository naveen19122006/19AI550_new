# Ex.No: 10  Implementation of 2D/3D game -------------------
### DATE:                                                                            
### REGISTER NUMBER : 
### AIM: 
To develop a game -------------------------in Unity 
### Algorithm:
🎮 Procedure to Use AIShooting.cs in Unity
✅ 1. Create a New Unity Project
Open Unity Hub.

Click New Project → choose 3D Core → give it a name (e.g., "AIShootingGame").

Click Create.

✅ 2. Create the Player
In Hierarchy: Right-click → 3D Object → Capsule (or any shape).

Rename it to Player.

Move it to a visible area (e.g., Position (0, 1, 0)).

In Inspector: Click Tag → Add Tag → type "Player" → save.

Select the Player object again → assign tag "Player".

✅ 3. Create the AI Enemy
Right-click → 3D Object → Cube (or any shape).

Rename it to EnemyAI.

Position it a bit far from the player (e.g., (0, 1, 10)).

✅ 4. Create Fire Point (Where the Bullet Spawns)
Right-click on EnemyAI → Create Empty → Rename to FirePoint.

Move it in front of the cube (e.g., Position (0, 1, 1) relative to EnemyAI).

This will be used as the shooting point.

✅ 5. Create the Bullet Prefab
Right-click in Hierarchy → 3D Object → Sphere.

Rename it Bullet.

Add a Rigidbody (Inspector → Add Component → Rigidbody).

Disable Use Gravity.

Add the Bullet.cs script (given earlier) to destroy it after a few seconds.

Drag the Bullet object into the Project panel to make a Prefab.

Delete the Bullet from the scene.

✅ 6. Create the AIShooting Script
In Project → Right-click → Create → C# Script → Name it AIShooting.

✅ 7. Assign the Script to the AI
Select EnemyAI in Hierarchy.

Click Add Component → choose AIShooting.

Drag:

The Player GameObject into the Player field.

The Bullet prefab from Project into the Bullet Prefab field.

The FirePoint (child of EnemyAI) into the Fire Point field.

✅ 8. Test the Scene
Press Play.

The EnemyAI should:

Detect the player.

Look at the player.

Shoot bullets toward the player when within range.

🛠️ Optional Enhancements:
Add player movement.

Add health system to player.

Add obstacle detection (e.g., using raycasts).

Add AI patrol before detecting player.
### Program:
AIShooting.cs
```
using UnityEngine;

public class AIShooting : MonoBehaviour
{
    public Transform player;               // Reference to player
    public GameObject bulletPrefab;        // Bullet prefab
    public Transform firePoint;            // Where bullets come from
    public float shootingRange = 10f;      // Shooting distance
    public float fireRate = 1f;            // Bullets per second
    public float bulletSpeed = 20f;        // Bullet speed

    private float nextFireTime = 0f;

    void Update()
    {
        if (player == null) return;

        float distance = Vector3.Distance(transform.position, player.position);

        if (distance <= shootingRange)
        {
            transform.LookAt(player);

            if (Time.time >= nextFireTime)
            {
                Shoot();
                nextFireTime = Time.time + 1f / fireRate;
            }
        }
    }

    void Shoot()
    {
        GameObject bullet = Instantiate(bulletPrefab, firePoint.position, firePoint.rotation);
        Rigidbody rb = bullet.GetComponent<Rigidbody>();
        rb.velocity = firePoint.forward * bulletSpeed;
    }
}

```
Bullet.cs
```
// Bullet.cs
using UnityEngine;

public class Bullet : MonoBehaviour
{
    void Start()
    {
        Destroy(gameObject, 3f); // Destroy after 3 seconds
    }
}

```
### Output:
![image](https://github.com/user-attachments/assets/5345f471-65da-41e9-91f8-52ab6b9afb9d)

### Result:
Thus the game was developed using Unity and adopted _-----------AI technology.
