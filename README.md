# ADS1-Assignment-3
Population and Health
"function to read in files in the Worldbank format returning original and transposed format"
df1 = wb.data.DataFrame(ind1, country_codes, mrv=60).T
df1 = df1.fillna(df1.median())
df1.head()
cls = df1.columns.tolist()
plt.figure(figsize=(12,6))
plt.title('Population Density by Year')
plt.plot(df1[cls[0]],"r--",label=cls[0])
plt.plot(df1[cls[1]],"m-",label=cls[1])
plt.plot(df1[cls[2]],"bo",label=cls[2])
plt.xlabel("Year")
plt.xticks(rotation=90)
plt.ylabel("Population Density")
plt.legend(loc='best')
plt.grid()
plt.show()
df2 = wb.data.DataFrame(ind2, country_codes, mrv=60).T
df2 = df2.fillna(df2.mean())
df2.head()
cls2=df2.columns.tolist()
plt.figure(figsize=(12,6))
plt.title('Heath Expenditure by Year')
plt.plot(df2[cls2[0]],"r--",label=cls2[0])
plt.plot(df2[cls2[1]],"m-",label=cls2[1])
plt.plot(df2[cls2[2]],"bo",label=cls2[2])
plt.xlabel("Year")
plt.xticks(rotation=90)
plt.ylabel("Heath Expenditure")
plt.legend(loc='best')
plt.grid()
plt.show()
"function for data normalization for the best fit"
def normal(data):
    minmax=MinMaxScaler()
    nrm=minmax.fit_transform(data)
    return nrm
nrml=normal(df1.values)
