# Game Using Unreal Engine 5

tutorial reference:
https://www.youtube.com/watch?v=e_SPuvO_l1w

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