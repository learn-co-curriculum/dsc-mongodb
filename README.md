# MongoDB Atlas

## Introduction
In this lesson, we will learn about the popular NoSQL database __MongoDB__. In particular, we will discuss __MongoDB Atlas__, a cloud-based database server with a free tier for learners. This is the perfect way to explore MongoDB's functionality while simultaneously getting a taste of what its like to utilize a cloud-based service.

We will also cover essential functions you will need to perform to interact with data in a NoSQL database. You can remember these skills using the acronym __CRUD__, or in other words:

- Create a MongoDB database with MongoDB Atlas
- Read data from a MongoDB database
- Update data from a MongoDB database
- Delete data from a MongoDB database

## Learning Objectives
You will be able to:

* Identify and describe the structure of a MongoDB record
* Perform CRUD operations in MongoDB Atlas GUI
* Perform CRUD operations in MongoDB Atlas in a Jupyter notebook with Python

## The Structure of a MongoDB Record
As we learned in the previous lesson on NoSQL databases, MongoDB is a __Document Store__. Each record is a JSON document, which can in turn contain other JSON documents in a nested format. 

For intance, here's an example record we might see in a MongoDB database: 

```json
{
   _id: ObjectId(8af37bd7891c)
   title: 'MongoDB Lab', 
   description: 'Introductory lab on how to use MongoDB',
   by: 'Flatiron School',
   topics: ['mongodb', 'database', 'NoSQL', 'JSON'], 
   sections: [	
      {
         section:'Introduction',
         dateCreated: new Date(2019,3,1),
         reading_time_minutes: 1 
      },
      {
         user:'Installing and Running MongoDB',
         dateCreated: new Date(2019,3,1),
         reading_time_minutes: 5
      }
      {
         user:'Examining a Sample MongoDB Record',
         dateCreated: new Date(2019,3,1),
         reading_time_minutes: 8
      }
   ]
}
```

This is more common than you might realize. If you open this file, `index.ipynb`, in a text editor, you'll see that each Jupyter Notebook is structured the exact same way, with each cell and everything it contains being embedded in the larger overall document.

Since we already have experience working with JSON, we'll see that it will actually be quite easy to work with data in MongoDB!

## Perform CRUD Operations in MongoDB Atlas GUI Online
To ease into using MongoDB, let's quickly create a database using the __MongoDB Atlas GUI (graphic user interface)__ to perform some CRUD operations in MongoDB. Then, once we have a basic understanding of MongoDB's functionality we can dive into performing CRUD operations in MongoDB with Python. The basic steps are as follows:

* Create a MongoDB Atlas account
* Create and connect to a __cluster__ in MongoDB Atlas
* Build a database and configure your cluster
* Load sample data to your MongoDB Atlas database

After we complete these steps, we can perform CRUD operations with MongoDB Atlas GUI online. 

### Create a MongoDB Atlas Account
1. The first step is to create a __MongoDB Atlas__ account, which will allow us to explore MongoDB in the cloud instead of installing MongoDB to our local machine. This approach will help you in three ways:
    * It simplifies the setup and configuration which will allow us to __begin performing _CRUD_ operations more quickly__.
    * It provides you with __experience working with cloud based tools__ which are becoming increasingly more common in the industry.
    * It gives you __free access to computational resources__ on a shared server which may allow your code to __run faster__ than it would on your local machine. 


2. To create an account, visit [MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register?utm_source=google&utm_campaign=search_gs_pl_evergreen_atlas_core_prosp-brand_gic-null_amers-us_ps-all_desktop_eng_lead&utm_term=mongodb%20atlas&utm_medium=cpc_paid_search&utm_ad=e&utm_ad_campaign_id=12212624338&adgroup=115749704063&gclid=Cj0KCQiAvqGcBhCJARIsAFQ5ke4Wxh0EcYUXOyhVoKfyoJmRhx-9eFm49z9whf6iOg08k5CTEzlDD58aAmMrEALw_wcB)
    * Enter your information to create an account. Then, verify your email address. 
    * You will be prompted to log in with your new account. 


3. Now, you should see the __Welcome screen__ (see the image below). Enter the following parameters to answer the questions on the welcome screen.
    * What is your goal today? __Learn MongoDB__
    * What type of application are you building? __No Application__
    * What is your preferred language? __Python__

<div><center>
<!-- ![MongoDB Atlas](https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/mongodb2.png) -->
<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/mongodb2.png" alt="A screen shot of the Welcome to Atlas screen on the MongoDB website. The screen contains a form with three questions: What is your goal today? What are you building? What is your preferred language." height=400 width=700/>
</td></tr></table>
   </center></div>

#### What is a cluster?
After completing step 1 and step 2 you will have created __Cluster0__. Let's discuss what a cluster is, then we can provision some resources and build a database!

In data science, we often perform operations that are __computationally expensive__. 
* This means that it takes a powerful computer to be able to process the information quickly or at all! 
* This can be especially true when it comes to working with large datasets, bulky files, and/or complex algorithms.

In the past, performing operations that were especially computationally expensive required a lot of overhead, which included creating __clusters__ or groups of computers that were networked together to distribute the computational burden and process the information more quickly.
* In cloud computing this concept is **virtualized** which allows users to connect to clusters remotely in order to use more powerful compute resources and storage space (among other benefits). 
* Users connect to storage and compute resources via their web brower or desktop application.
* This lowers the up-front cost of building, maintaining, and using a database by allowing companies to pay for resources based on their needs instead of spending lots of cash on servers that may not be appropriate for their needs in the long term. 

A __shared server__ is a server that is provisioned to multiple users at once. 
* This means that the data and applications of many users are stored on the same server and share computer resources.
* At times, there will be variability in how fast or slow your queries are executed depending on how many users are using the server at a given time.
* Shared servers are a cost effective way to **sandbox** or experiment with using cloud services before paying for dedicated resources. Databases, applications, and websites that have high demands for compute resources, storage, or security will generally opt for a __dedicated server__.

### Create a Database in MongoDB Atlas
Now that we have a MongoDB account, we can begin using MongoDB Atlas.

1. Next, select __Build a Database__.
<!-- ![alt text](https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/mongodb4.png) -->
<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/mongodb4.png" alt="A screenshot of the MongoDB Atlas Database Deployment page before a database has been created. It contains a large green button in the center of the screen that reads `Build a Database`"  height=400 width=700/>
</td></tr></table>


2. You will be redirected to a screen that displays the different price tiers for MongoDB Atlas. We will be using __Shared__ which is the free tier. Select __Create__ from the Shared pane on the right side of your screen. 
<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/mongodb5.png" alt="A screenshot of the MongoDB Atlas price tier screen with the Shared tier highlighted with a red border around it."  height=400 width=700/>
</td></tr></table>


3. You will be directed to a page called __Create a Shared Cluster__ where you will configure settings for your cluster. What you might choose in the future will vary by use case, but for our purposes we will use AWS as the cloud provider. Then, select the region that is closest to you as your region. You should now be on the __Security Quick Start__ screen.
<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/mongodb6.png" alt="MongoDB6" height=400 width=700/>
</td></tr></table>

### Access Permissions
In order to use your MongoDB Atlas database, you will need to follow these steps to grant permissions for your computer to access your MongoDB server remotely. The options you might use in the future may vary by use case.

1. The next screen, Security Quickstart, will allow you to configure permissions for your MongoDB Atlas cluster and database. Use the following options for the specific items mentioned below. Leave any other items on the default setting. Use the images as a guide:
    * Authentication Method: __Certificate__
    * Common Name: __learn-cert__
    * Download Certificate When User is Added: __On__
    * Specific Privileges: __readWriteAnyDatabase__

<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/mongodb8.png" alt="MongoDB8" height=400 width=700/>
</td></tr></table>

##### Important!
**After you select __Add User__ your TLS certificate will download. Put your TLS certificate in your home directory. This is your computer's "passport" for accessing MongoDB Atlas. We will need the file path later.**
    
2. Then, we will select where we would like to connect from. Choose __Local Environment__. 

3. Under the heading __Add entries to your IP Access List__ select the button that reads __Add My Current IP Address__. Then select __Finish and Close__.
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/mongodb10.png" alt="MongoDB10" height=350>

Since we turned on the option to download our certificate upon creation, check the your downloads folder to ensure a CERT file appears. Keep that file handy -- we will need it again soon.

Now you've successfully granted access permissions to your MongoDB Atlas server!

### Basic CRUD Operations in MongoDB Atlas GUI
There is a lot we can learn about MongoDB and NoSQL databases by exploring the MongoDB Atlas GUI and downloading some sample data to our database. Later on, we can expand on these skills by learning how to execute them with Python. 

### Creating a Database
To get familiar with MongoDB, let's begin with a sample dataset. Here are a few important things to remember:
Keep in mind, that just as a SQL database has tables, a Mongo database has collections of __documents__, which can be various kinds of files. In our case, our documents are similar to records which are data stored in key value pairs (like a JSON file or a Python dictionary).

1. To begin, start on the __Data Deployments__ page and select __Browse Collections__. You will be redirected to the __Collections__ page. 

3. In the center of the screen, you will see a prompt. Choose __Load a Sample Dataset__. 
    * __This may take 5-10 minutes to load__.
    
<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/mongodb13.png" alt="MongoDB8" height=400 width=700/>
</td></tr></table>
    
After completing these steps, you will have created several databases by loading the sample dataset. 

### Reading Data

#### Select a Collection
1. Once loaded, navigate to the left-hand side of the screen to the __Collections Pane__.
* At the top of the Collections pane, we can see the number of databases and the number of collections among all the databases.
* Directly underneath, you will notice that there is a button to __Create a Database__.
* Below this, you will find a search bar and the list of databases. Each database name expands to display the collections in that database.


2. To begin, click on the database __sample_airbnb__ in the Collections pane on the left side of your screen. 
* This will display the metadata for sample_airbnb in Cluster0. 
* On this screen we can view the size of sample_airbnb as well as the various collections that exist within the database (in this case, we only have __listingsAndReviews__).
<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/mongodb18.png" alt="MongoDB8" height=400 width=700/>
</td></tr></table>



3. Click on the collection __listingsAndReviews__ and wait for the documents to load. You will notice that the structure of the record is very similar to the file we examined above (under _The Structure of a MongoDB Record_).
<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/mongodb19.png" alt="MongoDB8" height=400 width=700/>
</td></tr></table>

#### Construct a Query with the Filter Box
We can construct simple queries in the __Filter box__, which is highlighted below. MongoDB queries resemble Python dictionaries and accept various modifiers to refine what data is selected. We will explore these further in the next lesson.

4. Let's suppose we want to construct a query that will allow us to select AirBNB documents containing listings that can accommodate 4 people and a room type that is the entire home or apartment. We can enter the query below into the Filter box: 
~~~~
{'accommodates': {'$gt': 3}, 'room_type': 'Entire home/apt'}
~~~~

You might notice that this query contains a modifier __$gt__, which indicates _greater than_. We will explore modifying queries in the next lesson.

<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/server2.png" alt="MongoDB8" height=300 width=700/>
</td></tr></table>
Now, we have retrieved only records that match our criteria. In the next lesson, we will explore how to construct more complex queries with MongoDB using Python.

### Updating Data
1. To update a record using the MongoDB Atlas GUI, simply locate the record and hover over the right corner. Use the query below to locate the record we will update. Construct a query to filter results for documents with an __id__ of __'10006546'__.
       
2. If you hover your cursor around the right corner of the document, a menu bar will appear.
<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/server2.png" alt="MongoDB8"  height=300 width=700/>
</td></tr></table>



3. Select the edit button (pictured below).
<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/edit-bar.png" alt="MongoDB8" height=100>
</td></tr></table>

4. Then, select the field you wish to modify. In our case, it is __'interaction'__.
    
5. Then, replace the value of __interaction__ as per the revisions below.

__Change__

~~~
Cot - 10 € / night Dog - € 7,5 / night` to `Cot - 12 € / night Dog - € 7,5 / night
~~~

to

~~~
Cot - 10 € / night Dog - € 7,5 / night` to `Cot - 15 € / night Dog - € 7,5 / night
~~~

### Deleting Data
To delete data from your database, hover in the right upper corner of the record you want to delete. Then, simply click the delete icon from the menu bar, pictured below.

<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/mongodb_lesson/delete-bar.png" alt="MongoDB8" height=100>
</td></tr></table>


Great! Now we have performed CRUD operations using MongoDB Atlas GUI.

## Summary
In this lesson, we examined the structure of a MongoDB record and described cloud computing terms like cluster and shared server. Then, we created a MongoDB Atlas account and performed CRUD operations on a sample dataset using the MongoDB Atlas GUI online. Next, we will build on our knowledge by connecting to our MongoDB Atlas database and perform CRUD operations in Python.
