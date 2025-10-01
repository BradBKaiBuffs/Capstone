Bradley Kai

CIDM 6395
FA 2025
Assignment 3

My experience in Software Systems has faciliated improvement in coding, the ability to be versatile and gain more experience in development, database integration and basic machine learning. I am most confident in the following areas:

# Areas I am most confident in

* **Python & Google Colab**: I became more proficient in writing and testing Python code in both local and cloud-based environments. Datacamp.com courses helped me brush up on the basic and intermediate Python skills that I would need for projects and assignments. I got to practice skills that would be used in some areas for companies:

```python
# Bradley Kai
import sqlite3
import csv


# read csv file
print("Reading customers.csv file.")
with open("customers.csv") as file:
    file_reader = csv.reader(file)

# and convert into list or tuple so I decided tuple
    customer_data = tuple(file_reader)
#    print(customer_data)

# import records into chinook.db customer table
db_name = "chinook.db"
with sqlite3.connect(db_name) as conn:
# went with the order in csv matching database columns in customer's table
    sql_command = "INSERT INTO Customers (Company, FirstName, LastName, Address, City, PostalCode, Country, Email) VALUES (?, ?, ?, ?, ?, ?, ?, ?)"
# for loop to go through each row
    for item in customer_data:
       customer_values = item
       conn.execute(sql_command, item)
    conn.commit()
    print("All done")

```
* **Web Development**: I practiced and applied my skill in building responsive, user-friendly interfaces using HTML5, CSS and Bootstrap. I become more familarized with layout design and accessibility. I found datacamp.com and www.w3schools.com useful in recalling basic concepts that I had forgotten due to lack of practicing.
* **Django Framework**: I implemented models, views, templates and other skills integretrated with SQL databases. https://docs.djangoproject.com/en/5.2/ documention was helpful in understanding specific information I needed through my weekly assignments. This help me build a site for a degree checklist project. An snippet of code shown below:
```Django
from django.contrib import admin
from checklist.models import(Student, Course, Major, Requirement, Enroll, Major_requirement, Major_selection, Course_requirement)

# Register your models here.
admin.site.register(Student)
admin.site.register(Course)
admin.site.register(Major)
admin.site.register(Requirement)
admin.site.register(Enroll)
admin.site.register(Major_requirement)
admin.site.register(Major_selection)
admin.site.register(Course_requirement)
```
* **SQL & SQL DB Browser**: I was very confident in designing and querying relational databases, integrating SQL with Django and using SQL DB Browser for schema integrated SQL databases. Once again, datacamp.com was instrumental in helping me practice the basic and intermediate concepts for SQL and related areas. In DB Browser, I was able to view database structures and execute SQL code for my project.
<img width="784" height="772" alt="image" src="https://github.com/user-attachments/assets/e8df279b-94a4-4f88-b6d9-e2c230fc27b0" />

* **GitHub**: I became more confortable using GitHub for collaboration, version tracking and project documentation. I practiced functions that were very applicable to daily tasks that apply to production environments like commits and pull requests. https://docs.github.com/en was a great resource to finding information on basic concepts needed to use GitHub.
* **User Stories & Data Models**: I learned and applied how to translate user requirements into technical specifications and designed data models that reflected business logic and relationships.
<img width="699" height="720" alt="image" src="https://github.com/user-attachments/assets/d8f889de-126e-4c28-81cc-9ff1dbd0a0d6" />

# Areas I'm weak in/Need more confidence with
---
These are the areas which I feel less confident and would benefit a lot with further practice or expsoure:
* **Security Best Pracices**: I understand basic authentication and authorization, but I would like a deeper dive into secure coding practices, encryption and vulnerability testing.
* **Scalability and Performance Optiimization**: I have built functional systems, but I want to learn more about caching, load balancing, and optimizing performance for high-traffic applications.
* **DevOps and CI/CD Pipelines**: I have deployed projects for my courses manually but I have not had hands-on experience with automated deployment tools like Jenkins, GitHub Actions or Docker.
* **Object-oriented concepts**: I'm not too confident when it comes to classes, objects and inheritance concepts. I know these concepts are a foundation for more advanced programming.
* **List Comprehension**: I still don't fully understand the concept of list comprehsion for Python. When the logic involves multiple nested loops or complex conditional statements, I find that it becomes difficult to understand.
   
# What I wish I knew
---
* **API Rate Limiting and Throttling**: I'd like to learn tools like Postman to test APIs. I'd also would like to implement basic limits using tools in AWS and Azure.
* **Services Architecture**: I'd like to gain experience in services like monolithic or microservices. This would mean exploring tools like Docker and Kubernetes.
* **Regular expressions**: Learning regular expressions would help me develop the abilty to search, manipulate and extra information from strings based on patterns. This should help with cleaning data, extration, data validation and data validation.

# Summary statement of capabilities, competencies and preparedness
---
Every project or assignment that I've built and successfully completed has involved aspects of software systems. Whether it was front-end interfaces to back-end logic and database integration, I have moved towards the goal of mastery with each step. These fundamentals have been layers of a canvas that allows me to apply my knowledge in future projects that are more complex. 

# Prepardness for portfolio and prototype representative project
---
I am prepared to apply what I learned in my Software System courses in my capstone prototype and portfolio. My strengths in Django, web development and machine learning integration positoin me to build scalable, intelligrent applications. I still have areas that I need to grow in but I have built a foundation an drive where I can learn on the go as I progress through a project.

# How Software Systems integrates
---
* **For Data Analytics**: Machine learning models and dashboards are often embedded into web applications to deliver inights in real-time and are interactive.
* **For Data Management**: Backend systems rely on structured databases.
* **For Networking and Cybersecurity**: Web applications must be secure and efficient.

# Software Systems Statement
---
Software systems are the platform where data, intelligence, and security join and transform information into great user-driven experiences.


