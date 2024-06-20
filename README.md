
# Attribute System 


#### To ensure the extensibility of the component, the Attribute System itself does not contain any game logic. It is solely responsible for managing value modifications, queries, and network synchronization. This design prevents any conflicts with other functionalities in your project, allowing you to safely use it in any project. The component has undergone extensive testing to support a wide range of requirements.
#### The demo provides numerous examples, such as the usage of Combat Buff and Equipment.
#### All data in component uses Array `Array<Map<Key, Value>>`
| ArrayName| Map Key | Map Value |
| ----------- | ----------- | ----------- |
| `BaseAttributeArray` |  `GameplayTag` |  `Float` 
| `BuffAttributeArray` |  `GameplayTag` |  `Float` 
| `EquipAttributeArray` |  `GameplayTag` | `Float` 
| `VariableArray` |  `GameplayTag` | `Float` 
| `TagArray` |  `Name` | `GameplayTag`  
| `FloatArray` |  `Name` | `Float` 
| `NameArray` |  `Name` | `Name`  
| `VectorArray` |  `Name` | `Vector` 
| `RotatorArray` |  `Name` | `Rotator` 
| `TransformArray` |  `Name` | `Transform` 

**The usage is very simple; you just need to add CT_Cmpt_Attribute to the Actor.**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/32f995e8-77cc-4302-994e-5af593fa70ae)


-------

**Potential Misunderstanding： In the documentation, "Inc" is an abbreviation for "Increase"**
```
var health = 100

function IncHealth(value){
  health = health + value
}

IncHealth(-10) // health = 90
IncHealth(50) // health = 140
```

-------

# Attribute 
**Attributes can be used to manage basic properties such as attack, defense, and maximum health. To differentiate sources, attributes are split into `Base`, `Buff`, and `Equip`.**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/38167d13-4234-45b2-b096-6e3c713f7ecb)

**`GetAttribute` will return the sum of `Base`, `Buff`, and `Equip`. For example, if a character's base `health` is 100, `Buff` adds 100, and `Equip` adds 100, the maximum `health` of the character will be 300.**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/4fe6ff6b-6360-48bc-be9e-f58f12839ac8)

## Attribute Rules
**In Rules, you can configure an attribute to affect the value of another attribute. For example, 1 Strength = +10 Maximum Health & +1 Health Regen & +1 Attack Power**
![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/085a2c50-dbd5-4af5-960d-ae05c6e7ff0f)

**Example**
![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/83b184ca-9b7e-4d34-b915-b7c7883f5c18)


**Base Attributes default support load from DataTable**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/92c81387-478b-41d4-bfd9-627a8874c3ae)

**In the DataTable example, different attributes are assigned to each character level.**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/060751b8-2412-4c9c-9037-2a0bdbcb8fdd)

**load attributes from DataTable**
![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/83ff0e5c-cb9a-4868-b38f-f456044aedd4)


**Modifying DataTable**
![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/1a41a695-87b6-497f-b9fd-c00f1e90aef5)


-------


# Variable


-------


**Variable is a special type that can interact with Attributes.**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/794583cd-8753-4337-b1db-dfb889c496f7)


# Rules
**Variable Rules are the rules that apply when Attributes change.**
![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/051a81d1-5f25-4fbc-84a2-f91cf35317e4)

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/716d32ec-22e8-421f-af55-7490b303f042)



| Type | Description |
| ----------- | ----------- |
| `None` |  Do nothing
| `AddToAttribute` | This variable will become part of the Attribute, i.e., GetAttribute = Base + Buff + Equip + Variable
| `Auto-Adjust` | When the Attribute changes, the Variable will also change accordingly. For example, if the Attribute increases by 10%, the Variable will also increase by 10%.

**Example**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/ec37ce54-f94a-41f0-9736-2478a6e72bf6)


-------

# Other Values


-------
**Additionally, you might need other types of attributes. This component provides some basic variable types for you to use.**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/6caaef77-1203-466f-897a-611ef428432f)


![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/c476fefd-0412-430c-ba80-df8d3219cb93)

**You might notice the absence of Boolean, Byte, Integer, String, and Text. You can use Float and Name instead.**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/1771784c-1f25-4381-9a26-29eeac436f2d)

**Example**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/f5cfd50a-7e3a-4b44-8e9b-077eaf55ecb8)


# Save Attribute
**Note: Attributes are not saved.**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/57607334-a596-4515-baed-746aa8938470)

**If you want to control the save logic yourself, use the following functions.**

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/f3fe4ebd-e92e-4201-9f89-da1411bf0e08)





-------

# Events

-------

![image](https://github.com/chaintree7/Event-driven-Game-Framework/assets/87846878/65f17e6d-d5b6-41fa-9a19-e94e0556dd15)

| Event | Description |
| ----------- | ----------- |
| `Event_OnBeginPlay` |  Component begins initialization
| `Event_OnInitialized` | Component completes initialization
| `Event_OnAttributeChanged` | When an Attribute changes
| `Event_OnVariableChanged` | When a Variable changes
| `Event_OnFloatValueChanged` | When a FloatValue changes
| `Event_OnNameValueChanged` | When a NameValue changes
| `Event_OnTagValueChanged` | When a TagValue changes
| `Event_OnVectorValueChanged` | When a VectorValue changes
| `Event_OnRotatorValueChanged` | When a RotatorValue changes
| `Event_OnTransformValueChanged` | When a TransformValue changes
| `Event_OnSaveGame` | When preparing to save the game
| `Event_OnSavedGame` | When the game is saved
| `Event_OnLoadGame` | When preparing to load the game
| `Event_OnLoadedGame` | When the game is loaded
