import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dataframe = pd.read_csv("swiggy 2.csv")
print(dataframe.head())

dataframe.info()

dataframe.describe()

dataframe.drop_duplicates(inplace=True)
dataframe

dataframe.drop("Address",axis=1,inplace=True)
dataframe

dataframe.drop_duplicates(inplace=True)
dataframe

plt.figure(figsize=(120, 600))

plt.hist(dataframe['Area'], bins=5)
plt.title('Area Distribution')
plt.xlabel('Area')
plt.ylabel('Frequency')
plt.xticks(rotation=90)

plt.show()

plt.figure(figsize=(12, 6))
plt.hist(dataframe['City'], bins=5)
plt.title('City Distribution')
plt.xlabel('City')
plt.ylabel('Frequency')
plt.xticks(rotation=90)

plt.show()

city_restaurant_counts = dataframe.groupby('City')['Restaurant'].count()
plt.figure(figsize=(12, 6))
plt.bar(city_restaurant_counts.index, city_restaurant_counts.values, color='skyblue')
plt.xlabel("City")
plt.ylabel("Number of Restaurants")
plt.title("Number of Restaurants in Each City")
plt.xticks(rotation=90)
plt.show()

plt.figure(figsize=(100, 600))
bars = plt.bar(dataframe['City'], dataframe['Restaurant'], color='skyblue')

# Annotate each bar with the number of restaurants
for bar in bars:
    yval = bar.get_height()  # Get bar height (restaurant count)
    plt.text(bar.get_x() + bar.get_width()/2, yval, int(yval),
             ha='center', va='bottom', fontsize=12, color='black')

# Labels and Title
plt.xlabel("City")
plt.ylabel("Number of Restaurants")
plt.title("Number of Restaurants in Each City")
plt.xticks(rotation=90)
plt.yticks(rotation=20) # Rotate X-axis labels to prevent overlap

# Show Plot
plt.show()

plt.figure(figsize=(10, 500))
sns.lineplot(data=dataframe, x='City', y='Restaurant', marker='o')

plt.title("Delivering time of different cities")
plt.xticks(rotation=45)
plt.yticks(rotation=45)
plt.show()

plt.figure(figsize=(10, 5))
sns.lineplot(data=dataframe, x='Delivery time', y='City', marker='o')

plt.title("Delivering time of different cities")
plt.xticks(rotation=45)
plt.show()

plt.figure(figsize=(10, 5))
sns.lineplot(data=dataframe, x='Avg ratings', y='Total ratings', marker='o')

plt.title("Delivering time of different cities")
plt.xticks(rotation=45)
plt.show()

max_row1= dataframe[dataframe["Avg ratings"] == dataframe["Avg ratings"].max()]
max_row1

new_dataset = max_row1.copy()

xyz = new_dataset[(new_dataset["Avg ratings"] == new_dataset["Avg ratings"].max()) &  (new_dataset["Delivery time"] == new_dataset["Delivery time"].min())]
xyz

xyz1 = new_dataset[(new_dataset["Avg ratings"] == new_dataset["Avg ratings"].max()) & (new_dataset["Price"] == new_dataset["Price"].min())]
xyz1

plt.figure(figsize=(10, 5))
sns.lineplot(data=new_dataset, x='City', y='Restaurant', marker='o')

plt.title("Delivering time of different cities")
plt.xticks(rotation=45)
plt.yticks(rotation=45)
plt.show()

plt.figure(figsize=(10, 5))
sns.lineplot(data=new_dataset, x='Delivery time', y='Restaurant', marker='o')

plt.title("Delivering time of different cities")
plt.xticks(rotation=45)
plt.yticks(rotation=45)
plt.show()

plt.figure(figsize=(10, 10))
sns.lineplot(data=new_dataset, x='Food type', y='Restaurant', marker='o')

plt.title("Delivering time of different cities")
plt.xticks(rotation=90)
plt.yticks(rotation=45)
plt.show()

plt.figure(figsize=(10, 10))
sns.lineplot(data=new_dataset, x='Food type', y='Price', marker='o')

plt.title("Delivering time of different cities")
plt.xticks(rotation=90)
plt.yticks(rotation=45)
plt.show()

plt.figure(figsize=(10, 10))

plt.plot(new_dataset['Area'] , marker='o')
plt.title('Area Distribution with 5.0 rating ')
plt.xlabel('Frequency')
plt.ylabel('Area')
plt.xticks(rotation=90)

plt.show()

plt.figure(figsize=(10, 10))

plt.plot(new_dataset['City'] , marker = 'o')
plt.title('City Distribution with 5.0 rating')
plt.xlabel('Frequency')
plt.ylabel('City')
plt.xticks(rotation=90)

plt.show()

