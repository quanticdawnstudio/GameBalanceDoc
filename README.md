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
 
  ### * 2.1 Creating and setting up the spreadsheet:<a name="passo1.1"></a>
  -   Within the root of your project, create a folder named **DATA** and within it create an **Excel** file spreadsheet.
