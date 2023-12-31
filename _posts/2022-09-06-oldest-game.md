---
layout: post
title:  "Portal"
summary: "Final Project for Game Programming"
date:   2023-11-30 15:39:40
preview: /assets/PortalGame/PortalGamePreview_Image.png
---


## 3D Game Development

- Coded in C++ and used SDL2 library for the Game development
- Implemented 3D collision detection system.
- Implemented basic player movement. 
- Applied the concept of Quaternion to solve the complicated FPS rotation and Camera Vision
- Focus on Portal Teleportation and Damage Mechanism
- Coded 3D Sound System and HUD for Game leading
- Created Enemy AI with a State Machine involving 5 states 


![Picture 1](/assets/PortalGame/PortalGameImage.png)

- Implemented classes for HUD game substitles and voice guidline
- Complete level loading mechanics 
- Use matrix transformation to transform between object's relative position and world position
- Use mouse input from the SDL class and concepts of yaw, pitch to implement FPS camera 

![Picture 2](/assets/PortalGame/PortalGamePellet.png)

- Turrets and laser shooting
- Applied linear segment cast for lasers to determine target within range.
- Used actor parenting between the TurretHead and the TurretBase  

![Picture 3](/assets/PortalGame/CreatingPortal.png)
- Implemented function of clicking LMB creates portal and clicking RMB makes orange portal. 

![Picture 4](/assets/PortalGame/GreenPellet.png)
- Implemented diffrent actor subclasses for diffrent in-game obejects and functionalities
  - energy catcher 
  - energy launcher 
  - pellet 
  - energy glass 
  - energy cube 

![Picture 5](/assets/PortalGame/Teleportation.png)

- Applied the transformations to fix the player's yaw after portal teleportation 
<details>
  <summary>Detailed Code for Transformation</summary>

  ### Code for fixing player's position
  ```C++
  playertoIn.Normalize();
				//Get the inverse world transform matrix of the “in” portal.
				Matrix4 inverseWorldTransform = GetWorldTransform();
				inverseWorldTransform.Invert();
				//Use Vector3::Transform to transform (1) by (2), making sure to pass in 0.0f for the third parameter.
				Vector3 outDir = Vector3::Transform(playertoIn, inverseWorldTransform, 0.0f);
				//Create a Z rotation matrix rotating by Math::Pi
				Matrix4 zRotation = Matrix4::CreateRotationZ(Math::Pi);

				Vector3 outDirRotated = Vector3::Transform(outDir, zRotation, 0.0f);
				Vector3 outDirInWorld = Vector3::Transform(outDirRotated,
														   outportal->GetWorldTransform(), 0.0f);

				outDirInWorld.Normalize();

				Vector3 eyepos = outportal->GetPosition() - 5.0f * outDirInWorld;
				Vector3 targetpos = outportal->GetPosition() + 5.0f * outDirInWorld;
				Matrix4 worldTransform = outportal->GetWorldTransform();
				Vector3 up = worldTransform.GetZAxis();

				mPortalViewMatrix = Matrix4::CreateLookAt(eyepos, targetpos, up);

				// outforward should not be the forward of the portal, instead, it should come from the calculation process that we just did
				Vector3 outForward = outDirInWorld;
				outForward.z = 0.0f;
				outForward.Normalize();
				float yaw = Math::Acos(Vector3::Dot(Vector3::UnitX, outForward));
				if (Vector3::Cross(outForward, Vector3::UnitX).z > 0.0f)
				{
					yaw *= -1.0f;
				}
				mOutYaw = yaw;
				return mPortalViewMatrix;
  ```
</details>






[For complete code, please click this Link to the Portal Game on my GitHub](https://github.com/itp380-20233/labs-Peter00796/tree/master/Lab12)

