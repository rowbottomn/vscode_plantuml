# Using PlantUML in VS Code to make UML Class Diagrams
### TLDR 
- Add the extension to VSCode: PlantUML Previewer
- Use this document to create .puml files for your class diagrams
- use CTRL-P to see the image generated.
---
Section| Topic | Author | Date
|---|---|---|---
1.0|[Purpose of the Tree Identification App](#1.0-purpose-of-the-tree-identification-app)|NR|02-20-23
2.0|[Login Authentification](#2.0-login-authentification)| NR| 02-22-23
3.0|[Storage of Tree Images](#3.0-storage-of-tree-images) |NR|02-25-23
4.0|[Storage of Tree Traits and Tree Data](#4.0-storage-of-tree-traits-and-tree-data)| NR | 02-25-23|
5.0|[Hosting of the App](#5.0-hosting-of-the-app) | NR | 02-18-23| 01-07-23
6.0|[AODA Concerns](#6.0-aoda-concerns)|NR| 02-20-23 | 


# 1.0 Purpose of the Tree Identification App
<details>
  <summary>
  * Design Need for the TreeID App 
  * Why not Machine Learning?
  * Basic Algorithm
  </summary>
  
  ### Design Need for the Tree ID App
  The app design came out of a request from Six Nations Lifelong Learning for an app which would help Hodinoso:ni people that do not have access to the language and cultural resources to help them regain that knowledge.  Many Hodinoso:ni people due to the colonization process enacted by multiple levels of governments in the past do not have access to language and culture; either through forced adoptions, the residential school system or the disenfranchisement of educated men or woman that married off-reserve.  This app was then seen as a first step in the attempt to create tools to support language and cultural revitalization.  While initially the app had a much larger scope of doing many medicinal plants and to include more cultural information like stories and medicinal uses, the scope was cut back as we discovered we were missing many institutional pieces like how to properly gatekeep sensative cultural knowledge and language from inappropriate access and potential liability from people not using the app to properly identify medicines and food plants.  Trees with just language was chosen as a deep enough problem to allow to encounter the data souveignty issues while shallow enough to avoid liability problems.
  A web app was chosen as it would allow students from STEAM Academy's PTECH (Pathways in Technology, Early College in High School) program to assist in the development of the program as they had a course in web development.  A web app also allows the app to run on virtually any smart device.  Lastly, a web app approach removes the need to have separate development for iOS and Android devices.

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

