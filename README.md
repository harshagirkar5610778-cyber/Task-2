import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv(r"C:\intern\titanic\train.csv")
print(df.head())
print(df.shape)
df.info()
print(df.isnull().sum())
print(df.duplicated().sum())
df["Age"] = df["Age"].fillna(df["Age"].median())
df["Embarked"] = df["Embarked"].fillna(df["Embarked"].mode()[0])
df = df.drop("Cabin", axis=1)
survival_count = df["Survived"].value_counts()
plt.bar(["Not Survived", "Survived"],
[survival_count[0], survival_count[1]])
plt.title("Titanic Survival Count")
plt.xlabel("Survival Status")
plt.ylabel("Number of Passengers")
plt.show()
