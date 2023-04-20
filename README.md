# Game Balance Documentation

  - This is the official documentation of the Game Balance plugin, an incredible plugin that can be used mainly to assist with balancing your game. With it, you can change all the values of your game in real-time through an Excel spreadsheet.
  

 
 ## Table of Contents

  <blockquote>
  <ol dir="auto">
  <li><a href="#Init">How the Game Balance Plugin works</a></li>  
  <li><a href="#passoa">Step-by-step guide to Game Balance operation</a><br> 
  2.1 - <a href="#passob">Creating and setting up the spreadsheet</a>  <br> 
  2.2 - <a href="#passo1.2">Table formatting</a> <br> 
  2.3 - <a href="#passo1.3">Configuring Game Balance Inside Unreal Engine</a> <br> 
  <li> <a href="#passo2">Adding the Game Balance Component</a> <br> 
  3.1 - <a href="#passo2.1">Adding the Game Balance Component in Blueprint</a>  <br> 
  3.2 - <a href="#passo2.2">Adding the Game Balance Component in C++</a>  <br> 
  <li> <a href="#passo3">General rules about the Game Balance Component</a>  <br> 
  4.1 - <a href="#passo3.1">Understanding the UpdateValues and what it is used for</a> <br>	  
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.1.1 - <a href="#passo3.1.1">Using UEnum in Game Balance</a> <br>
  <li><a href="#passo4">Running the Game Balance</a> <br>
  5.1 - <a href="#passo4.1">Creating the variables in practice</a> <br>
  5.2 - <a href="#passo4.2">Playing the GameBalance</a> <br>
  5.3 - <a href="#passo4.3">Cool things about Game Balance</a> </li>
  

<ol dir="auto">
<ol dir="auto">

</blockquote>

 


 ## 1. How it works<a name="Init"></a>

-   Game Balance uses the reflection system of the Unreal Engine to find the actors and variables that should have their values changed in real-time from a .csv file created from an Excel spreadsheet. This is a complex system that uses the UnrealBuildTool and UnrealHeaderTool to perform the entire process. It's important to note that, by accessing the variables directly from the virtual memory, these values have no permanent effect. They only serve during the game session so that you can find the appropriate values and then change them with confidence that you have found the correct values.

 ## 2. Step-by-step guide to Game Balance operation:<a name="passoa"></a>
 
 -   For the perfect operation of GameBalance, it is necessary to pay attention to some steps. Follow each step carefully to be able to use GameBalance effectively.
 
  ### * 2.1. Creating and setting up the spreadsheet:<a name="passob"></a>
  -   Within the root of your project, create a folder named  **`Data`** and within it create an **`Excel`** file spreadsheet.
   <blockquote>
 
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/Captura%20de%20tela%202023-03-27%20122549.jpg)
  </blockquote>
  
 -   Yes, you can name the file whatever you like, but make sure you remember the name so you can access it later.
 
  <blockquote>
  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/raw/main/Ima/Captura%20de%20tela%202023-03-27%20122800.jpg)
  </blockquote>
  
  ### * 2.2. Table formatting<a name="passo1.2"></a>:

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
  
  ### * 2.3. Configuring Game Balance Inside Unreal Engine:<a name="passo1.3"></a> 
      
  - After activating the Game Balance plugin, you will need to go to the Project Settings and search for "World Settings Class". Select the                               "GameBalanceWorldSettings" from the dropdown menu, and then restart the engine. This step is important because it ensures that the Game Balance logic is properly       integrated into the game world and that the updated values from the Game Balance table will be applied during gameplay.
   <blockquote>
  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/WorldSettings.jpg)
  </blockquote>

  - Once you have configured the GameBalanceWorldSettings class, you can go to the World Settings window for your level and set the TableName property to the correct name of your .csv file. To do this, open the World Settings window by selecting "World Settings" from the "Settings" menu in the Unreal Editor. Then, scroll down to the Game Balance section and find the TableName property. Enter the name of your .csv file in the field provided.
  
  <blockquote>
  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/TableName.jpg)
  </blockquote>

## 3. Adding the Game Balance Component<a name="passo2"></a>
 
  - After completing the initial setup, we need to define which Actors will be recognized by the Game Balance system. To do this, we will use the GameBalanceComponent, and there are two ways to add it: using C++ code or using Blueprint. After that, we will look at the variables that should be included to be recognized by the reflection system.
  
   ### * 3.1. Adding the Game Balance Component in Blueprint:<a name="passo2.1"></a> 
  
  - To add the GameBalanceComponent using Blueprint, follow these steps:
  
  <blockquote>
    
   1. Open the Blueprint for the Actor that you want to add the GameBalanceComponent to.
   2. In the Components panel, click the "Add Component" button and search for "Game Balance".
   3. Click on the "Game Balance" component to add it to your Actor.
 
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/addacbp.jpg)
  </blockquote>
  
   ### * 3.2. Adding the Game Balance Component in C++:<a name="passo2.2"></a> 
	
  - Before anything else, we need to add the GameBalance to the list of modules inside the **`.Build.cs`** file of your project.
  <blockquote>
  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/build.jpg)
  </blockquote>
	
    
  - Write the following code in your actor's **.header**:
  <blockquote> 
	  
  ```ruby
  private:
  UPROPERTY(VisibleAnywhere, BlueprintReadOnly, Category = GameBalance, meta = (AllowPrivateAccess = "true"))
  class UGameBalanceComponent* GameBalanceComponent;
  
  public:
  FORCEINLINE class UGameBalanceComponent* GetGameBalance() const {return GameBalanceComponent; }
  
  UFUNCTION()
  void UpdateValues();
  ```
    
   - In the example above, we are instantiating the GameBalanceComponent in private. Then, with a FORCEINLINE, we create a getter function so that we can access it          from anywhere we want. We also create a function called UpdateValues(), which will be used later `(it is important to remember to put UFUNCTION on this function, as it will be called by a delegate)`.
    
  </blockquote>
  
  -  Write the following code in your actor's **.cpp**:
  
   <blockquote> 
	   
```ruby   
 #include "GameBalanceComponent.h"
  
 YourCostructor::YourConstructor()
  {
     GameBalanceComponent = CreateDefaultSubobject<UGameBalanceComponent>(TEXT("GameBalance"));
     AddOwnedComponent(GameBalanceComponent);
     GameBalanceComponent->OnUpdateValuesInContainer.AddDynamic(this, &AMyProjectCharacter::UpdateValues);
  }   
 ```
    
   - In the example above, we are instantiating the GameBalanceComponent in private. Then, with a FORCEINLINE, we create a getter function so that we can access it          from anywhere we want. We also create a function called UpdateValues(), which will be used later `(it is important to remember to put UFUNCTION on this function, as it will be called by a delegate)`.
    
  </blockquote>
     
## 4. General rules about the Game Balance Component:<a name="passo3"></a>
     
   - Here are some general rules about the Game Balance Component:
<blockquote>   
	
  1. Only variables with specific types can be modified by the Game Balance Component, including **`integers`**, **`floats`**, **`booleans`**, **`names`** and               **`UEnum`**.
  2. Only variables that are marked as **`"UPROPERTY"`** in the class header file can be modified.
  3. If a variable has a custom **`setter`** or **`getter`**, it will not be modified by the Game Balance Component.
  4. The **`variables that are modified`** by the Game Balance Component must have the same name as the property in the .csv file.
  5. It's important to make sure that the **`Excel spreadsheet or .csv file is closed before running Game Balance.`** This is because Game Balance needs exclusive          access to the file in order to read the data and update the game variables in real-time. If the file is open in Excel or another program, it may be locked and          inaccessible to Game Balance, leading to errors or unexpected behavior. Therefore, it's best to close the file before launching Game Balance to ensure that it can      properly access and utilize the data in the file.
  6. The actor that contains the variables must have a **GameBalanceComponent** **`attached to it`**.
  7. "It is not possible to change **`float`** and **`enum`** values through blueprints."
 </blockquote>
 
 ### *4.1. Understanding the UpdateValues and what it is used for<a name="passo3.1"></a>
 
  - The UpdateValues function is called whenever we execute the Game Balance, and it serves two purposes:
  
   1. Internal variables of external components can only be updated through an accessory variable, for example: the MaxWalkSpeed variable is inside the                     CharacterMovement component, so in order to update it we need to create another variable, which was the 'Speed' float that we created in earlier sections, and         then we will do the following in this case:
   <blockquote>
    
   ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/MaxValue.jpg)
  </blockquote>
  
  #### *4.1.1. Using UEnum in Game Balance.<a name="passo3.1.1"></a>
   - UEnum variables have their own template for being updated, as they are more complex than other variables, since each UEnum is handled differently. To update a          UEnum, we will also need the UpdateValues function of GameBalance.
   <blockquote>
    1 - First, you will create your UEnum normally, remembering that in order to work, it must have the specifier UPROPERTY(). <br>
    
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/soenum.jpg)
    
   2 - Then, inside UpdateValues, you will use the following code: <br>
    
 ```ruby	   
   YourEnum = GetGameBalance()->UpdateEnumProperties<EYourEnum, AYourActorClass>(YourEnum, this)   
  ```

   In the end, it will look something like this:
    
   ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/UpdateValues%20Completo.png)
  </blockquote>
    3 - You can also use UpdateValues in BP, in this case, you will access the Update directly from the component that will be called OnUpdateValuesInContainer. It             will be accessible by clicking on the component in the BP, within Events in the component details. 
<blockquote>
  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/UpdateValuesBP.jpg)
	Of course, by using BP, you will not be able to request an update for any UEnum.
 </blockquote>
	   
## 5. Running the Game Balance:<a name="passo4"></a>
 
  -  Now that we know everything about Game Balance, it's time to put our knowledge into practice. To do so, I'm going to create a test project to demonstrate all the      variables and peculiarities of Game Balance in practice.
  
  ### 5.1. Creating the variables in practice<a name="passo4.1"></a>
  
   - Firstly, I created a variable of each type supported by Game Balance, taking into account the limitations as shown below:<br> 
    **a** -  I created a **`bool`** type variable, a **`Name`** type variable, and an **`int`** type variable in BP, as they are compatible with creation in BP but can              also be created in C++.
  <blockquote>
    
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/raw/main/Ima/variables%20bp.jpg)
  </blockquote>
 
   **b** - In C++, I created two float type variables and a UEnum that will contain only 3 information, that of Red, Black, and Green."
      
  <blockquote>
    
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/c%2B%2B%20%20variables.jpg)
  
  **`IMPORTANT: Remember that float type and UEnum variables are only captured by Game Balance if they are created in C++ and have the UPROPERTY() ecification."`**
  </blockquote>
	   
 ### 5.2. Playing the GameBalance.<a name="passo4.2"></a>
- Before we play, we must make sure of some things we have already discussed above, such as:
  <blockquote>
   1 - We have updated the information in our spreadsheet. <br>   
	  
   ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/planilha%20atualizada.jpg)   
   I'll show you how it looks now just so there's no doubt about how the spreadsheet should be filled out.
	  
  2 - That our .csv file is **`CLOSED`** and has been created through **`EXCEL`**.
	  
  3 - The correct name of our .csv file is filled in the TableName field of the WorldSettings.
	  
  ![](https://github.com/quanticdawnstudio/GameBalanceDoc/raw/main/Ima/TableName.jpg)

  </blockquote>

 - Just to make it easier for demonstration, I created a WBP to make all the changes we will make visible.
  <blockquote>
	 
   ![](https://github.com/quanticdawnstudio/GameBalanceDoc/raw/main/Ima/image.jpg)

  </blockquote>
	   
 - Now you just need to hit play on your project and press the **`Game Balance Execute button`**.
  <blockquote>
	
   ![](https://github.com/quanticdawnstudio/GameBalanceDoc/raw/main/Ima/Game%20Balance%20Button.jpg)
 
If for some reason it's not showing up in the location indicated above, it can be found in the location indicated below:
   ![](https://github.com/quanticdawnstudio/GameBalanceDoc/raw/main/Ima/GBInWindows.jpg)

  </blockquote>

  - If everything goes well, when you press the button a success message will be displayed.
  <blockquote>
	 
   ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/sucesso.jpg)

  </blockquote>

   - Otherwise, an error message will be displayed and it will mention one of the possible errors that we have already considered in this documentation.
   <blockquote>
 
   ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/error%20mensage.jpg)

  </blockquote>
	   
### 5.3. Cool things about Game Balance:<a name="passo4.3"></a>
  - I prepared a gif that shows the Game Balance in action.
  <blockquote>
	 
   ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/ok.gif)

  </blockquote>
	   
   - One cool thing about Game Balance is that you don't need to stop the game to change the values in the table. Check out the gif below to see how I change the            values in the table and then update them without needing to end the session.
  <blockquote>
	
	Notice that I put a wrong value in the CheckBox variable, and Game Balance simply ignores it without presenting any errors.
	
   ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/completo.gif)

  </blockquote>
  
   - Now let's see a situation where an error message may appear, which in the case below, is when I pass the name of a non-existent worksheet.
   
   <blockquote>
	
   ![](https://github.com/quanticdawnstudio/GameBalanceDoc/blob/main/Ima/error.gif)

  </blockquote>
 
   
   

**Know the Plugin: https://www.unrealengine.com/marketplace/en-US/product/c4a9d518eda84a4cb2d1eb9f59f6f88e**
     



  
