# Using PlantUML in VS Code to make UML Class Diagrams
### TLDR 
- Add the extension to VSCode: PlantUML Previewer
- Use this document to create .puml files for your class diagrams
- use CTRL-P to see the image generated.
- drag the image to the url bar in chrome to get an image you can download or save.
---
Section| Topic | Author | Date
|---|---|---|---
1.0|[The PlantUML VS Code Extension](#the-plantuml-vs-code-extension)|NR|03-02-23
2.0|[Class Diagram Basics](#class-diagram-basics)| NR| 03-02-23
3.0|[Relationships Between Classes](#relationships-between-classes) |NR|03-02-23
4.0|[Class Diagram Extras](#class-diagram-extras)| NR | 03-02-23|
5.0|[Getting Your Image](#gettting-the-image) | NR | 03-02-23



# 1.0 The PlantUML VS Code Extension
<details>
  <summary>
  * Setup in VS Code<br>
  * File Setup<br>
  * Getting the Preview
  </summary>
  
  ### Setup in VS Code
  Click on extensions in the VS Code sidebar

  ### Why Not Machine Learning?
  When first conceptualizing the app, there was a strong desire to explore using machine learning (ML) tools to build a ML model capable of recognizing the different plants and to use this for the purposes of identification.  After exploring the proper scope of the need described above, it became apparent that what was needed was a tool to help human intelligence to learn to properly identify the trees rather than an app which utilized machine intelligence to replace the human capability.

  ### Basic Algorithm
  So the "Guess Who" algorithm was developed where we give a selection of trees and a human uses their own senses to narrow down the possibily candidates.  Users select traits based on drop down lists for Leaves, Bark and Buds.  The gallery of candidates possess a large selection of images of each part which can be used to help the use make the determination based on comparisons. When they have isolated it down to only one choice: the user has identified their tree and will see the name of the tree in Cayuga and Mohawk.
  
</details>

# 2.0 Login Authentification
<details>
  <summary>
  * Firebase Email Authentification 
  * Passing the Token
  </summary>
  
  ### Firebase Email Authentification
   The authentification is offloaded to Google Firebase Authentification Libraries. In its current form, the app does not have much need for authentification.  Basically, it is used to keep a unique identifier which could be used for tracking future id's.  However, it also serves as a testbed for building best practices for gatekeeping the cultural knowledge.  Only in the event that a person passes the authentification process, will they get access to the words, images and traits.
   Multiple solutions for online storage were considered. Many indigenous language projects go 'dark' 
 after funds dry up.  A longlasting, free or nearly free solution was required.
 - W3Storage allows the app to store the tree data in FileCoin, a cryptocurrency that is 'mined' by providing storage.
 - Firebase from Google provides cheap, effective app storage for free if use is below a specifc threshold.  

  ### Passing the Token
  Successful authentification will supply 3 sets of needed tokens/IDs: 
  1. The Server uses a Firebase token to authenticate the user and supply the client with the other needed access IDs to access the actual images directly from Firebase Storage and the files from the W3Storage.
  2. The W3Storage token for the tree list and the list of tree traits. The tree list is used to pull the images and make the tree slides.  The tree traits list is used to generate the drop down lists.
  3. Firebase IDs are given to the client to allow access to the images stored for each tree.    
</details>

# 3.0 Storage of Tree Images
<details>
  <summary>
  * Why Images are Needed
  * Method of Image Collection
  * Firebase Storage Usage
  </summary>
  
  ### Why Images are Needed
  In learning how to identify trees, there is a considerable amount of information that needs to be conveyed so it can happen reliabily.  Users will not know what doubly palmate means for instance.  The idea was that by offering a large sampling of images that features the parts of the tree being used to identify the trees, that it would allow users to get a general sense of what the traits mean and also what they look like at various times of the year and various stages of development.

  ### Method of Image Collection
  Images were collected via a web scraping program which searched for images from Google Image Search for each term (for example: *slippery elm bark*).  A machine learning model then removed images that seemed cartoonish 
 or that contained people or words that might indicate ownership. All other images were assumes to be available for non-commercial use.  No one assumes or indicates ownership of the images. 
  ### Firebase Storage Usage
  The images were uploaded to a Firebase Storage account. See image below:
  ![Firebase Storage Files for Images](./docs/documentation_images/firebase_storage.png)
  Images were stored separately by bark, buds or leaves for each tree. 
  ![Firebase Storage Files for Images](./docs/documentation_images/firebase_storage1.png)

</details>

