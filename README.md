# Creating-Knowledge-Graph-Storing-in-Graph-DB

Knowledge Graph :
A knowledge graph is a structured representation of information that connects entities and their relationships. It's essentially a semantic network where nodes represent entities (like people, places, things, or concepts) and edges represent the relationships between them (like "is_a", "has_part", "located_at").

Key characteristics of a knowledge graph:

Entities: The basic building blocks of a knowledge graph. They can be concrete objects (e.g., people, places, things) or abstract concepts (e.g., ideas, theories). Relationships: The connections between entities. They describe how entities are related to each other (e.g., "is_a", "has_part", "located_at"). Properties: Additional information associated with entities or relationships (e.g., attributes, values). How knowledge graphs are used:

Question Answering: Knowledge graphs can be used to answer complex questions by following the relationships between entities. Recommendation Systems: By analyzing the relationships between entities, knowledge graphs can recommend relevant items to users. Semantic Search: Knowledge graphs can improve search results by understanding the semantic meaning of queries and returning more relevant results. Data Integration: Knowledge graphs can be used to integrate data from multiple sources and provide a unified view of information. Examples of knowledge graphs:

Google Knowledge Graph: Used by Google Search to provide more informative and relevant search results.

DBpedia: A knowledge graph extracted from Wikipedia data.

Freebase: A large-scale knowledge graph developed by Google.

Implementation : 

# Step1 : Create the example folder structure with the respective files :

a. app.py : It is the executable file locally run through streamlit

b. entity_relationship_extraction.py : The logic for entity relationship extraction , which LLM to leverage and parsing llm response content

c. visualize_graph.py : It has the definition of how the knowledge graph should look like

d. newyork.txt and raw_text.txt : This are sample .txt file which are used to create knowledge graph feel free to update with your specific .txt file and point to it .

e. neo4j_db.py : This file manages the storage of entities and relationships in Neo4j. In this file, we define a class, Neo4jHandler, which is used to manage interactions with a Neo4j database. The class allows us to store entities and relationships extracted from our dataset into Neo4j in a structured and efficient way.

# Step 2 : Update the following parameters in the file 

Update your OPEN AI Key and choice of model in entity_relationship_extraction.py . In model i considered "gpt-4o-mini" , you can update with your choice .

client = OpenAI(api_key="OPEN AI - API KEY")

response = client.chat.completions.create( model="gpt-4o-mini", messages=messages, )

Point to the .txt file of choice in app.py

text_file_path = "raw_text.txt"

Graph database connection details : 

# Neo4j connection details
neo4j_uri = " "  
neo4j_user = " "
neo4j_password = ""

# Step 3 : run the requirements.txt file ( command : pip install -r requirements.txt

# Step 4 : run the streamlit app locally ( command : streamlit run app.py )

Visually you will see the following components :

Section 1 : It will highlight the extracted entities , a partial snapshot below .

![image](https://github.com/user-attachments/assets/cecbb9d9-6789-458d-ae73-9635cf28fce6)

Section 2 : It highlights the Extracted relationship tuples , a partial snapshot below .

![image](https://github.com/user-attachments/assets/6914d7be-9936-4c86-b188-f1bacdd38163)

Section 3 : Visualization of the knowledge graph .

![image](https://github.com/user-attachments/assets/316d2ea4-cfbf-4ccf-bc09-6b73ed799613)

Section 4 ; Click on the "store entities and relationships to Neo4j" button , it will store the results in graph database 

# Step 5 : Login to the graph database , in my case i am leveraging neo4j and visualize the knowledge graph : 

  command ( MATCH (n:Entity) RETURN n LIMIT 25; ) : It helps u see the entities ![image](https://github.com/user-attachments/assets/8d60cf80-2bd7-42b3-9d58-4847fbf1455b)

  command ( MATCH (n)-[r]->(m) RETURN n, r, m ) : it helps u see the nodes , relationships ..  

  ![image](https://github.com/user-attachments/assets/9207f5ac-148a-47f4-89d2-a589d5b1e1bf)

  ![image](https://github.com/user-attachments/assets/6ed544de-3bdc-43df-9b95-bff27d1d030a)


  Note : Create free Neo4j account : https://neo4j.com/docs/aura/auradb/getting-started/create-database/

  Happy coding :)


  















