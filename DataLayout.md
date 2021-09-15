## Data Layout

Data Modeling Tutorials : 
- https://www.youtube.com/watch?v=QAqK-R9HUhc
- https://www.youtube.com/watch?v=yuPjoC3jmPA
- https://www.youtube.com/watch?v=leNCfU5SYR8



### Steps to data modeling with MongoDB
1. Develop the Application
2. Define the Data Model based on Application
3. Improve the Application 
4. Improve the Data Model 
5. Repeat step 3 and 4 forever

### Method

- Data model is defined at the application level.
- Design is part of each phase of the application lifetime. When the application requirements changes, the data model changes too.
- What effects the data model?
    - The data that your application needs
    - Application's read and write usage of the data. If we need to read more or write more then optimize the data in such a way

### Step-by-step Iteration 
1. Evaluate the application workload 
    1. Look at the potential workload of future usage and where the application is going. 
    2. Look at current and predicted scenarios.
    3. Production logs and stats 
    4. By doing this, you understand : 
        - data size
        - database queries and indexes
        - current operations and assumptions

2. Map out the Entities and their Relationships
    1. CRD - Collection Relationship Diagram 
        - Link ?
        - Embeded ?






### Link vs. Embeded

Relationships: 

1. One to One
    - One to One Linked 
    ![One to One Linked](/images/onetoonelinked.png)
    - One to One Embeded
    ![One to One Embeded](/images/onetooneembeded.png)

2. One to Many
    - One to Many : Array in Parent
    ![One to Many : Array in Parent](/images/onetomanyarrayinparent.png)

    - One to Many : Scalar in Child
    ![One to Many : Scalar in Child](/images/onetomanyscalarinchild.png)

3. Many to Many
    - Many to Many : Array on either side
    ![Many to Many : Array on either side](/images/manytomanyarrayoneitherside.png)


















