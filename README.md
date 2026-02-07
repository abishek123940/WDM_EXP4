### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 07.02.2026
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program 1:
```
import pandas as pd
df = pd.read_csv("C:\\Users\\admin\\Downloads\\clustervisitor.csv")
df
cluster={"Young":(df['Age']<=30),"Middle":((df['Age']>30)&(df['Age']<=50)),"Old": (df['Age']>50)}
count=[]
for group,condition in cluster.items():
    visitors=df[condition]
    count.append(len(visitors))
    print(f"The visitors on {group} age are")
    print(visitors)
    print("count=",len(visitors))
import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.bar(['Young','Middle','Old'],count,color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:


<img width="546" height="728" alt="Screenshot 2026-02-07 142543" src="https://github.com/user-attachments/assets/34058f1d-b858-4743-a9e9-1c9e5fe413ef" />
<img width="478" height="121" alt="Screenshot 2026-02-07 142549" src="https://github.com/user-attachments/assets/dbcaa395-6738-4e4d-8ac3-0ddff01f8ff1" />
<img width="923" height="711" alt="Screenshot 2026-02-07 142559" src="https://github.com/user-attachments/assets/cda500d8-682c-4c0b-84bd-d7616fe67739" />


### program 2:
```
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
k=KMeans(n_clusters=4,random_state=55)
df3['cluster']=k.fit_predict(newdf)
df3
import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.scatter(x=df3['Age'],y=df3['Income'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title("Visitor Distribution in Different Clusters")
plt.show()
```
### Output:
<img width="293" height="797" alt="Screenshot 2026-02-07 142610" src="https://github.com/user-attachments/assets/d77b35d9-f740-4bd1-b2f4-6132069b67ea" />
<img width="236" height="232" alt="Screenshot 2026-02-07 142616" src="https://github.com/user-attachments/assets/9d5a0729-9276-4b3d-a2de-7e4ce2d9f0c8" />
<img width="924" height="704" alt="Screenshot 2026-02-07 142626" src="https://github.com/user-attachments/assets/1e94d461-4150-4328-96b2-3a9fc6d32450" />


### Result:
The implement Cluster and visitor Segmentation for Navigation patterns in python is execute successfully.
