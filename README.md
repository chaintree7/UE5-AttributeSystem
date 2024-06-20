
# Attribute System 


#### To ensure the extensibility of the component, the Attribute System itself does not contain any game logic. It is solely responsible for managing value modifications, queries, and network Replication. This design prevents any conflicts with other functionalities in your project, allowing you to safely use it in any project. The component has undergone extensive testing to support a wide range of requirements.
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

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/7dfaa4c1-aa56-44dc-9e21-c2ee03208172)



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

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/80ee9c3f-5f62-4ab1-8ca9-cbdc390c7bfb)


**`GetAttribute` will return the sum of `Base`, `Buff`, and `Equip`. For example, if a character's base `health` is 100, `Buff` adds 100, and `Equip` adds 100, the maximum `health` of the character will be 300.**

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/5c5cb3db-f786-439b-87cb-ba599d631524)


## Attribute Rules
**In Rules, you can configure an attribute to affect the value of another attribute. For example, 1 Strength = +10 Maximum Health & +1 Health Regen & +1 Attack Power**
![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/209a8573-870e-43be-b2a4-0ee42b525c70)


**Example**
![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/ae8f5170-48b0-49fa-9ff9-146d9d81608c)



**Base Attributes default support load from DataTable**

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/d8c9179f-7e13-4230-80db-40b9c41a35d1)


**In the DataTable example, different attributes are assigned to each character level.**

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/39d2ef06-f190-4404-9a96-0f143e6e2331)


**load attributes from DataTable**
![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/1cf12c80-1bb9-496d-84de-a78977e446e3)



**Modifying DataTable**
![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/1679489a-a848-4252-b3bd-3f7c24825fcd)



-------


# Variable


-------


**Variable is a special type that can interact with Attributes.**

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/f583799e-649c-42f0-b777-7137fd981b98)



# Rules
**Variable Rules are the rules that apply when Attributes change.**
![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/68576162-08fb-410b-a3c2-9a29541a3b7f)


![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/83185c23-2ef0-4b6b-a7e4-a8cbcdfd5962)




| Type | Description |
| ----------- | ----------- |
| `None` |  Do nothing
| `AddToAttribute` | This variable will become part of the Attribute, i.e., GetAttribute = Base + Buff + Equip + Variable
| `Auto-Adjust` | When the Attribute changes, the Variable will also change accordingly. For example, if the Attribute increases by 10%, the Variable will also increase by 10%.

**Example**

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/cd2d5285-7dbd-4268-879a-414f4b23968a)




-------

# Other Values


-------
**Additionally, you might need other types of attributes. This component provides some basic variable types for you to use.**

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/119c5e76-098e-4917-8874-a6ae253c6bed)


![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/b334934f-c9a9-4d4d-b389-f097be1e184d)


**You might notice the absence of Boolean, Byte, Integer, String, and Text. You can use Float and Name instead.**

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/9cd7377e-2769-44fd-8320-c1ad7c5b8a38)


**Example**

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/c76e0d14-6f56-4921-8909-c7ca2436b295)



# Save Attribute
**Note: Attributes are not saved.**

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/ec396a65-f230-44c7-b734-64a968415b7a)


**If you want to control the save logic yourself, use the following functions.**

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/ee6e6f5a-483e-4a7f-9d2f-105b3c836c50)






-------

# Events

-------

![image](https://github.com/chaintree7/EventDriven-AttributeSystem/assets/87846878/bab58e77-00cc-4bd9-adf3-70d2cdfd1545)


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
