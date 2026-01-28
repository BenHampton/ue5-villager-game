# Game Using Unreal Engine 5

tutorial reference:
https://www.youtube.com/watch?v=e_SPuvO_l1w

Git LFS .gitattributes and .gitignore:
https://dev.epicgames.com/community/snippets/rVBG/unreal-engine-git-lfs-gitattributes-and-gitignore

### Villager_BlendSpace1D
#### BlendSpace
- is an animation asset that will enable us to transition between different animations depending on the players speed
- in the Villager_BlendSpace1D add the animation assets to the control panel. hold Control and move mouse along the line between animations to see animation speed effect


## Walking-Running Speed:
### EventGraph:
Event BlueprintUpdateAnimation 
- loops and is called on every frame per second

### Try-Get Pawn Owner: 
- Gets the owner of the animation bp.
- i.e. in the BP_ThirdPersonCharacter if we select our mesh. The Anim class is ABP_Villager the owner is BP_ThirdPersonCharacter
- convert Vector to Float -> use Vector Length which is essentially seed


## Jumping:

### ABP_Villager
#### AnimGraph 
- where place all animation nodes

#### Even Graph
- where the logic lives to fill in for the animation
- creating locomotion -> state machine allows you to have mutiple animations states (idle walk jump)
- used Node Cast To BP_ThirdPersonCharacter (used as Character BP) which is a direct reference to the third person character (BP_ThirdPersonCharacter). this allowed 'Character BP' to have access to BP_ThirdPersonCharacter and get movement options like isFalling

### Additive Animation: 
plays an animation on top of another and merges them for a smooth transition


#### EnemyAI
Created BP_EnemyAI under Content
- In the CP Viewport under Mesh selected skin (villager)
    - to center skin, under Transform in the last fields set Location -89 and Scale -90

    -Attack
        - window -> FAB

- For single use animations, we can use Right Click the attack animation go to Create -> Create AnimMontage
    - then in the BP_EnemyAI with Ai Move To set up we can hook up the On Success  to the Play Montage to execute the AnimMontage
    - finally in the ABP_Willager we need to add a Default Slot between Locomotion and the Output Pose
        - this is bc AnimMontage are plays on a default slot

- Adding Knockback
    - Adding Sphere Trace By Channel which is a sphere that will go from one point to another

## Components 
- Branch - If statement
- Get Actor Location
- Get Actor Rotation and to get the location that its looking Get Forward Vector
