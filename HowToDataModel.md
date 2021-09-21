## How to Data Model with MongoDB

Data Modeling Tutorials : 
- https://www.youtube.com/watch?v=QAqK-R9HUhc
- https://www.youtube.com/watch?v=3GHZd0zv170
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
    - Look at the potential workload of future usage and where the application is going. 
    - Look at current and predicted scenarios.
    - Production logs and stats 

2. Map out the Entities and their Relationships
    - CRD - Collection Relationship Diagram 
        - [Link or Embed?](#link-vs-embeded)
        - To make this decision, answer these questions : 
            - How often does the embeded information get accessed?
            - Is the data queried using the embeded information?
            - Does the embeded information change often?
        ![Link or Embed](/images/linkorembed.png)

3. Finalize the data model for each collection 
    - Identify and apply relevant design patterns 
        1. The Schema Versioning Pattern
        2. The Bucket Pattern 
        3. The Computed Pattern with The Bucket Pattern 

- By doing these 3 steps, you get : 
    - data size
    - collections with documents fields and shapes of each
    - database queries and indexes
    - data model that's efficient with :
        - cost of data servers
        - time it takes to query data
        - easy of use for the developers
    - current operations assumptions and growth projections









### Link vs. Embeded

#### Relationships in SQL world: 
![One to One Linked](/images/relationships.png)

#### Relationships in NoSQL world: 
1. One to One
![One to One Linked](/images/onetoonelinked.png)
![One to One Embeded](/images/onetooneembeded.png)

2. One to Many
![One to Many : Array in Parent](/images/onetomanyarrayinparent.png)
![One to Many : Scalar in Child](/images/onetomanyscalarinchild.png) 

3. Many to Many
![Many to Many : Array on either side](/images/manytomanyarrayoneitherside.png)


### Conclusion

- Start small and imperfect
- Clean up the model as the application requires performance
- Grow the data model with the app
![Flexible Data Modeling](/images/flexibledatamodeling.png)















