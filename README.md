# Game Balance Documentation

  - This is the official documentation of the Game Balance plugin, an incredible plugin that can be used mainly to assist with balancing your game. With it, you can change all the values of your game in real-time through an Excel spreadsheet.
  
  
 
 ## Table of Contents

  <blockquote>
  <ol dir="auto">
  1 - <a href="#Init">How the Game Balance Plugin works</a>
<ol dir="auto">
<ol dir="auto">
<ol dir="auto">

</blockquote>




 ## 1. How it works<a name="Init"></a>

-   Game Balance uses the reflection system of the Unreal Engine to find the actors and variables that should have their values changed in real-time from a .csv file created from an Excel spreadsheet. This is a complex system that uses the UnrealBuildTool and UnrealHeaderTool to perform the entire process. It's important to note that, by accessing the variables directly from the virtual memory, these values have no permanent effect. They only serve during the game session so that you can find the appropriate values and then change them with confidence that you have found the correct values.

 ## 2. Step-by-step guide to Game Balance operation:<a name="passo1"></a>
 
 -   For the perfect operation of GameBalance, it is necessary to pay attention to some steps. Follow each step carefully to be able to use GameBalance effectively.
 
  ### * 2.1. Creating and setting up the spreadsheet:<a name="passo1.1"></a>
  -   Within the root of your project, create a folder named  **`Data`** and within it create an **`Excel`** file spreadsheet.
   <blockquote>
 
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/Captura%20de%20tela%202023-03-27%20122549.jpg)
  </blockquote>
  
 -   Yes, you can name the file whatever you like, but make sure you remember the name so you can access it later.
 
  <blockquote>
  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/raw/main/Ima/Captura%20de%20tela%202023-03-27%20122800.jpg)
  </blockquote>
  
  ### * 2.2. Table formatting:

  -   Now let's talk about how the table should be arranged. Pay close attention, because if something is wrong here, GameBalance may not work correctly.
The table should be organized with each row representing an item in the game, such as a character or weapon, and each column representing a different attribute or characteristic of that item.
For example, if you are creating a table for characters in your game, the columns could include attributes such as speed, health, damage output, special abilities, and so on. Each row would then represent a different character in the game, with values for each attribute filled in for that character.
It's important to keep the table consistent and organized, with clear labels for each column and row. This will make it easier to analyze and adjust the values to achieve the desired balance in the game.

  - **`Pay attention to the image below and the details of what each thing represents`**
  
   <blockquote>
  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/planilha.jpg)
    
   1. The first row of the first column should always be empty.
    This is because the first row is typically reserved for the column headers or labels, which describe the attribute being measured in each column. Since the first       column is typically used to list the items being measured (such as characters or weapons), it does not need a label in the first row.
    Leaving the first row of the first column empty will also make it easier to sort and analyze the data in the table, since it will be clear that the first row is       not a data point, but rather a placeholder for the item names.
    
   2. The first row of each column should contain the property names, or column headers, that describe the attribute being measured in that column.
    For example, if you are creating a table for characters in your game, the first row could include property names such as "Speed," "Health," "Damage Output," and so     on.
    Having clear and consistent property names in the first row of each column will make it easier to read and understand the data in the table, and will also make it     easier to sort and analyze the data.
    *`It's important that the actor in the game has a property with the same name as the property you are putting in the table. For example, if you have a "Speed" property in your table for characters in the game, then the character actor in the game should also have a "Speed" property that can be accessed and adjusted.`*
    
   3. In the first column, you will list the names of the classes that the reflection system will analyze to find the properties that will be adjusted.
   
   4. Below each property name in the first row, and following the column, you should enter the new value for that property. For example, if the first row contains the    property name "Speed" and you want to adjust the speed value for a specific character in the game, you would enter the new speed value for that character in the        cell below the "Speed" column for that character's row. By entering the new values in the table, you can easily adjust the properties for multiple items at once,      without needing to manually change the code for each individual item. This makes it easier to balance the game and adjust the values based on playtesting and          feedback.
  
  </blockquote>
  
 - To save as a .csv file, go to "File" and then "Save As". In the "Save As" dialog box, choose "CSV (Comma delimited)" from the "Save as type" dropdown menu, and then   choose the location where you want to save the file. Finally, click "Save" to save the file in .csv format.
 <blockquote>
  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/raw/main/Ima/Captura%20de%20tela%202023-03-27%20123029.jpg)
  </blockquote>
  
  ### * 2.3. Configuring Game Balance Inside Unreal Engine: 
      
  - After activating the Game Balance plugin, you will need to go to the Project Settings and search for "World Settings Class". Select the                               "GameBalanceWorldSettings" from the dropdown menu, and then restart the engine. This step is important because it ensures that the Game Balance logic is properly       integrated into the game world and that the updated values from the Game Balance table will be applied during gameplay.
   <blockquote>
  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/WorldSettings.jpg)
  </blockquote>

  - Once you have configured the GameBalanceWorldSettings class, you can go to the World Settings window for your level and set the TableName property to the correct name of your .csv file. To do this, open the World Settings window by selecting "World Settings" from the "Settings" menu in the Unreal Editor. Then, scroll down to the Game Balance section and find the TableName property. Enter the name of your .csv file in the field provided.
  
  <blockquote>
  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/TableName.jpg)
  </blockquote>

## 3. Adding the Game Balance Component<a name="Unreal"></a>
 
  - After completing the initial setup, we need to define which Actors will be recognized by the Game Balance system. To do this, we will use the GameBalanceComponent, and there are two ways to add it: using C++ code or using Blueprint. After that, we will look at the variables that should be included to be recognized by the reflection system.
  
   ### * 3.1. Adding the Game Balance Component in Blueprint: 
  
  - To add the GameBalanceComponent using Blueprint, follow these steps:
  
  <blockquote>
    
   1. Open the Blueprint for the Actor that you want to add the GameBalanceComponent to.
   2. In the Components panel, click the "Add Component" button and search for "Game Balance".
   3. Click on the "Game Balance" component to add it to your Actor.
 
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/addacbp.jpg)
  </blockquote>
  
   ### * 3.2. Adding the Game Balance Component in C++: 
	
  - Before anything else, we need to add the GameBalance to the list of modules inside the **`.Build.cs`** file of your project.
  <blockquote>
  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/build.jpg)
  </blockquote>
	
    
  - Write the following code in your actor's **.header**:
  <blockquote> 
  <pre>
  
  *private:*
  UPROPERTY(VisibleAnywhere, BlueprintReadOnly, Category = GameBalance, meta = (AllowPrivateAccess = "true"))
	class UGameBalanceComponent* GameBalanceComponent;
  
  *public:*
  FORCEINLINE class UGameBalanceComponent* GetGameBalance() const {return GameBalanceComponent; }
  
  UFUNCTION()
  void UpdateValues();
  </pre>
    
   - In the example above, we are instantiating the GameBalanceComponent in private. Then, with a FORCEINLINE, we create a getter function so that we can access it          from anywhere we want. We also create a function called UpdateValues(), which will be used later `(it is important to remember to put UFUNCTION on this function, as it will be called by a delegate)`.
    
  </blockquote>
  
  -  Write the following code in your actor's **.cpp**:
  
   <blockquote> 
  <pre>
  #include "../../Plugins/GameBalance/Source/GameBalance/Public/GameBalanceComponent.h"
  
  YourCostructor::YourConstructor()
  {
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;GameBalanceComponent = CreateDefaultSubobject<UGameBalanceComponent>(TEXT("GameBalance"));
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;AddOwnedComponent(GameBalanceComponent);
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;GameBalanceComponent->OnUpdateValuesInContainer.AddDynamic(this, &AMyProjectCharacter::UpdateValues);
  }
  </pre>
    
   - In the example above, we are instantiating the GameBalanceComponent in private. Then, with a FORCEINLINE, we create a getter function so that we can access it          from anywhere we want. We also create a function called UpdateValues(), which will be used later `(it is important to remember to put UFUNCTION on this function, as it will be called by a delegate)`.
    
  </blockquote>
     
## 4. General rules about the Game Balance Component:
     
   - Here are some general rules about the Game Balance Component:
<blockquote>   
	
  1. Only variables with specific types can be modified by the Game Balance Component, including **`integers`**, **`floats`**, **`booleans`**, **`names`** and               **`enumerations`**.
  2. Only variables that are marked as **`"UPROPERTY"`** in the class header file can be modified.
  3. If a variable has a custom **`setter`** or **`getter`**, it will not be modified by the Game Balance Component.
  4. The **`variables that are modified`** by the Game Balance Component must have the same name as the property in the .csv file.
  5. The actor that contains the variables must have a **GameBalanceComponent** **`attached to it`**.
  6. Cannot change a **float value** if it is created in **Blueprint**.
  
  
 </blockquote>
	   
## 5. Running the Game Balance:
 
     
     
  
