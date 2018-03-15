The first visualization, we use python3 do data clean(Jupyter). The file name is py.ipynb in the data process folder. We extracted “Enroll, Female: Average ACT Math Score” and “Enroll, Male: Average ACT Math Score”. The code is: 
df.dropna(subset=['Enroll, Female: Avg. ACT Math Score (Enrl F)'], inplace = True)
df.dropna(subset=['Enroll, Male: Avg. ACT Math Score (Enrl M)'], inplace = True)
Then we put the two attributes in one table and save it to “1.csv”. the code is:
df = df[['Enroll, Female: Avg. ACT Math Score (Enrl F)','Enroll, Male: Avg. ACT Math Score (Enrl M)']]
df.to_csv("1.csv",index=False)
In this graph we read dataset from “1.csv” in data folder. we want to find what kind of correlation about “Enroll, Female: Average ACT Math Score” and “Enroll, Male: Average ACT Math Score”. Our visualization X axis represent “Enroll, Female: Average ACT Math Score”, Y axis “Enroll, Male: Average ACT Math Score”. Through our graph, we can see. The best fit line closes to a straight line, which has a positive gradient. That means the two data have positive correlation. Normally, we think maybe male ACT math score better than female. However, through our graph, we can see when one variable increases the other increases. That means male and female do not have distinction.
The second visualization, we use python3 do data clean(Jupyter). The file name is Project-2-Z in data process folder. We extracted “Enroll, Female: Average HS GPA (Enrl F)”, “Enroll, Male: Average HS GPA (Enrl M)” and “School Year”. This part code is:
df.dropna(subset=['Enroll, Female: Average HS GPA (Enrl F)'], inplace = True)
df.dropna(subset=['Enroll, Male: Average HS GPA (Enrl M)'], inplace = True)
df.dropna(subset=['School Year'], inplace = True)
df['School Year'] = df['School Year'].str.split('-').str[0].astype(int)
Then we calculate “total average HS GPA”, the code is:
df['Average HS GPA'] = (df['Enroll, Female: Average HS GPA (Enrl F)'] + df['Enroll, Male: Average HS GPA (Enrl M)'])/2
The final step we put these data in one table and save the data to “2.csv”. The code is:
df = df[['School Year','Average HS GPA']]
df = df.sort_values(by="School Year", ascending=True)
df = df[["School Year", "Average HS GPA"]].groupby("School Year").mean()
df.to_csv("2.csv")
In this graph we read dataset from “2.csv” in data folder. we want to know the average high school GPA trend from 2003 to 2016, the X axis represent year (from 2003 to 2016) and the Y axis represent average high school GPA. Through our graph, we can see the min value is 3.49 on 2005, the max value is 3.757 on 2016 and this line trend is increasing.

The third visualization, we use python3 do data clean(Jupyter), the file name is yifan.ipynb in data process folder. We extracted “Major Program Name” and “Totals, Male: Total Declared Majors (Tot. M)”. This part code is:
MAJOR = data.groupby('Major Program Name')['Totals, Male: Total Declared Majors (Tot. M)'].count()
Then we save it to .csv file, the code is:
MAJOR.to_csv('Major.csv')
In this graph we read dataset from “Major.csv” in data folder. We want to show the total male students number in different major. This bar chart X axis is different majors, the Y axis is “Totals, Male: Total Declared Majors (Tot. M)”, through this graph we can see the most popular major for male students is computer science. 
The fourth visualization, we use python3 do data clean(Jupyter), the file name is Age.ipynb in data process folder. We extracted “School Year” and “Enroll, Female: Average Age (Enrl F)”. This part code is:
df.dropna(subset=['Enroll, Female: Average Age (Enrl F)'], inplace = True)
df.dropna(subset=['School Year'], inplace = True)
Then we put these data into one table and save it to “age.csv”, the code is:
df['School Year'] = df['School Year'].str.split('-').str[0].astype(int)
df = df[['School Year','Enroll, Female: Average Age (Enrl F)']]
df = df.sort_values(by="School Year", ascending=True)
df.to_csv("age.csv", index = False)
In this graph, we read dataset from “age.csv” in data folder. We want to show the age range from 2003 to 2016. The X axis is "School Year", the Y axis is “Enroll, Female: Average Age (Enrl F)”. Through we can see different age range for each year and we found the normal age difference is about 15 in each year. The max difference value happened in 2012.

The fifth visualization, we use python3 do data clean(Jupyter). The file name is yifan.ipynb in data process folder. We extracted “Enroll, Female: Avg. SAT Math Score (Enrl F)” and “Enroll, Male: Avg. SAT Math Score (Enrl M)”, and drop the miss value. The code is:
SAT_RAW = data[['Enroll, Female: Avg. SAT Math Score (Enrl F)', 'Enroll, Male: Avg. SAT Math Score (Enrl M)']]
SAT = SAT_RAW.dropna()
Then we put the two attributes in one table and save it to “SAT.csv”. the code is:
SAT.to_csv('SAT.csv')
In this graph we read dataset from “SAT.csv” in data folder. We want to find what kind of correlation about “Enroll, Female: Avg. SAT Math Score” and “Enroll, Male: Avg. SAT Math Score”. Our visualization X axis represent “Enroll, Female: Avg. SAT Math Score”, Y axis “Enroll, Male: Average SAT Math Score”. Through our graph, we can see. The best fit line closes to a straight line, which has a positive gradient. That means the two data have positive correlation. Normally, we think maybe male SAT math score better than female. However, through our graph, we can see when one variable increases the other increases. That means male and female do not have distinction.

Our team role:
Zhixin Chang:
Team leader.
Work with Yifan to generate required data for the third main bar chart visualizations by Python
Work with Yifan to design and draw the second bar chart visualizations on D3
Debug D3 and python problems from others.
Design the web page on D3
Integrate codes and data

Peng Yan:
Debug D3 and python problems from others.
Creating the styles for the HTML file.
Generate required data for the first main scatter plot visualizations
Design and draw the first scatter plot visualizations on D3
Writing the first, second, and forth part of the readme

Zening Li:
Generate required data for the second main line plot visualizations by Python
Generate required data for the average age and year scatter plot visualizations by Python
Design and draw the second line plot visualizations on D3
Design and draw the average age and year scatter plot visualizations on D3
Writing the third part of the readme

Yifan Li:
Work with Zhixin to generate required data for the third main bar chart visualizations by Python
Generate required data for the scatter plot visualizations by Python
Work with Zhixin to design and draw the second bar chart visualizations on D3
Design and draw the scatter plot visualizations on D3
