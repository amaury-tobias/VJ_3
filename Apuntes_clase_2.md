Un espacio de memoria reservado que implementa metodos y atributos de una clase

? poo factory

> Action
+ connect/create node
¬ select option on node
??? curiosity
"" variable

## DISPLAY BARS HUD
* Content > FirstPersonBP > Blueprints > FirstPersonCharacter
  - BeginPlay + create widget ¬ Game HUD ¬ Return Value >L Promote to Variable > "GameHUDReference"

* Content > FirstPersonBP > Blueprints > FirstPersonCharacter
  - Jump > pressed + Set "EnergyValue" = "EnergyValue" -= 0.05
  - ??? My Blueprint (Panel) > OJO > show inherit > characterMovement

## ELEMENTOS EN INVENTARO
* Content > UMG > Inventory Slot
  - Delete canvas
  - Inventory Slot > 
	Button> Imge > Create Binding(Function "GetInventoryImage") + "PickupImage" +> Make Brush From Texture ¬> Return Node
	Button > (Style: Normal Tint & Hovered Tint) > isEnabled : false
	Button > isEnabled > Create Binding (Function "InventoryCheck") + "PickupImage" +> isValid ¬> Return Node
  - Event Graph
	Button >Events >+ "OnClicked()"
	Button > Event Dispatchers + "ButtonWasClicked" > Inputs + "SlotClicked{Integer}" &+ "InventorySlot{Integer}"
	"ButtonWasClicked" >+ Call ¬ CallButtonWasClicked
	Variables + "InventorySlot{Integer}" > CallButtonWasClicked: SlotClicked

* Content > UMG > Game HUD
  - GameHUD +> Vertical Box "Inventory Menu" : isVariable
  - GameHUD
	Vertical Box "Inventory Menu"
		+> Text & Uniform Grid Panel
		+> Uniform Grid Panel +> "Slot_0"{InventorySlot} ... "Slot_4"{InventorySlot} ? Compilar InventorySlot
		> isEnabled : false & Visibility : Hidden
  - Variables + "ActiveInventory" {Boolean} : False (Bind isEnabled) & "InventoryVisible" {ESlate Visibility} : Hidden (Bind Visibility)
