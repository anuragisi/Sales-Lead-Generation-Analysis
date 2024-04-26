# Sales-Lead-Generation-Analysis

<b>Description:</b> The data used here, for Sales Qualified Leads Generated for FY 23-24

<b>Sales Owner:</b> 29 Sales Team member responsible for conversion of lead to customer.

<b>Entity Name:</b> Names of the 846 lead organization.

<b>Current Stage:</b>
  <ul>
        <li>1. Customer - Identified **45** potential customers who may be interested in the product/service, but not yet engaged.</li>
        <li>2. Proposal - Sending proposal to **64** potential customers.</li>
        <li>3. Qualified Lead (QL) - **721** customers/leads qualified by Sales Team as a genuine.</li>
        <li>4. Recently Qualified Lead (RQL) - **6** customers/leads recently qualified by Sales Team as a genuine.</li>
        <li>5. Unqualified Lead (UQL) - **10** customers/leads not qualified by Sales Team as a genuine, may further require nurturing.</li>
  </ul>

<b>Status</b>
<ul>
  <li>1. Active - 36 customers/leads, 18 proposals, 248 QL, 6 RQL, 4 UQL</li>
        <li>2. Free - 1 QL may have not been qualified further.</li>
        <li>3. Lost - 9 customer, 38 proposals, 257 QL, 4 UQL have decided not to proceed with the purchase.</li>
        <li>4. Nurture - 8  proposals, 215 QL, 2 UQL requires further nurturing to build their interest.</li>
</ul>
<b>Prospect Creation Date:</b>b> Date of identification of the entities through different channels.

<b>Lead Creation Date:</b> Date on which first positive response from that entities is received.

<b>QL Creation Date:</b> Date on which Sales Team marked them as a genuine customer/lead through defined process.

<b>Lost Date:</b> Date on which the customer/lead did not convert.

<b>Nurture Date:</b> Date on which customers/leads further nutured to build their intereest.

<b>Won Date:</b> Date on which customer/lead convert into QL.

<b>Channel:</b> 272 Emails, 278 LinkedIn, 113 Website, 74 Bidding, 40 Apollo.io, 19 Tender, 13 Paid, 3 Referral, 1 Cold call, 1 Job Board, 1 Nurturing, 31 No Channel Data Available.

<b>Lead Score:</b> Score of lead is calculated through defined formula to understand business potential from the lead.Higher the lead score, better the lead.

<p>Import Libraries</p>
<pre>
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt 
</pre>

<p>
  Loading Data
</p>
<pre>
  import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
</pre>
<p>
  View Dataframe
</p>
<pre>df</pre>
<p>
  Total Rows & Columns
</p>
<pre>df.shape</pre>
<p>
  Data Information
</p>
<pre>
  df.info()
</pre>
<samp>
  <img width="558" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/d3cedc07-8beb-4ec2-b9ee-41319abc9803">
</samp>
<p>
  <b>Data Quality Check</b>
</p>
<p>
  Duplicate Values
</p>
<pre>
  len(df[df.duplicated()])
</pre>
<samp>
  <img width="537" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/3c8a45b0-bd5e-4486-9f5c-b95dfd3562b1">
</samp>
<p>
  Missing Values/Null Values
</p>
<pre>
  print(df.isnull().sum())
</pre>
<samp>
 <img width="320" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/71a95ae0-129c-4118-8c30-d4dc7fa340fc">
</samp>
<pre>
  #Visualizing the missing values using heatmap
sns.heatmap(df.isnull(), cbar=False)
</pre>
<samp>
  <img width="620" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/7205b756-a92b-4e33-88c2-14c287eaaec5">
</samp>
<p>
  Incomplete Records:
</p>
<pre>
df = df.dropna(subset=['Prospect Creation Date'])
print(df.isnull().sum())
</pre>
<samp>
  <img width="468" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/de2dc39e-4122-4f05-b316-8d2a47d74214">
</samp>
<p>
  Variable Information
</p>
<pre>
  #Columns
df.columns
</pre>
<samp>
  <img width="699" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/9507ca17-f00d-4607-a228-0d308eac12b1">
</samp>
<pre>
  #Describe
df.describe(datetime_is_numeric=True)
</pre>
<samp>
  <img width="1430" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/d9412fb8-4ab8-4d70-ae5f-e292e03d221d">
</samp>
<pre>
  #Check unique values for each variable
for i in df.columns.tolist():
  print("No. of unique values in ",i,"is",df[i].nunique(),".")
</pre>
<samp>
  <img width="578" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/0368e45a-3d15-4159-b787-dd6cf797ed92">
</samp>
<p>
  <b>Analysis</b>
</p>
<p>
  Lead Source Analysis
</p>
<pre>
  df['Channel'].value_counts()
</pre>
<samp>
  <img width="336" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/a473a2c0-d957-41c1-8e44-295c68f00547">
</samp>
<pre>
  # Plot a bar chart
plt.figure(figsize=(10, 6))
df['Channel'].value_counts().plot(kind='bar', color='skyblue')
plt.title('Distribution of Channels')
plt.xlabel('Channels')
plt.ylabel('Frequency')
plt.xticks(rotation=45, ha='right')  # Rotate x-axis labels for better visibility
plt.show()
</pre>
<samp>
  <img width="705" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/13238cc0-13a6-4c57-83e5-decfc9eabcd8">
</samp>
<p>
  Comparing each Channels with mean Lead Score
</p>
<pre>
  # Count of unique channels
channel_counts = df['Channel'].value_counts().reset_index()
channel_counts.columns = ['Channel', 'Count']

# Median lead score for each channel
channel_lead = df.groupby('Channel')['Lead Score'].median().reset_index()
channel_lead.columns = ['Channel', 'Median Lead Score']

# Merge the two DataFrames on the 'Channel' column
channel_l = pd.merge(channel_counts, channel_lead, on='Channel')

channel_l
</pre>
<samp>
<img width="535" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/d5aefcd6-b1fd-4cfd-9647-3d2d8ace3117">
</samp>
<pre>
  # Plot a bar graph
plt.figure(figsize=(10, 6))
plt.bar(channel_lead['Channel'], channel_lead['Median Lead Score'], color='skyblue')
plt.xlabel('Channel')
plt.ylabel('Median Lead Score')
plt.title('Median Lead Score for Each Channel')
plt.xticks(rotation=45, ha='right')  # Rotate x-axis labels for better visibility
plt.grid(axis='y')
</pre>
<samp>
  <img width="702" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/2c05321f-9e6a-4646-8476-56b24d5b5497">
</samp>
<pre>
  # Count of unique channels
channel_counts = df['Channel'].value_counts().reset_index()
channel_counts.columns = ['Channel', 'Count']

# Median lead score for each channel
channel_lead = df.groupby('Channel')['Lead Score'].median().reset_index()
channel_lead.columns = ['Channel', 'Median Lead Score']
channel_lead = channel_lead.sort_values(by='Median Lead Score')

# Merge the two DataFrames on the 'Channel' column
result_df = pd.merge(channel_counts, channel_lead, on='Channel')

# Display the combined DataFrame
print(result_df)
</pre>
<samp>
<img width="534" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/b95fefbd-2b20-43bc-8bf3-1979a794dd58">
</samp>
<pre>
  # Larger plot size
fig, ax1 = plt.subplots(figsize=(25, 15))

# Bar plot for counts
color = 'tab:blue'
ax1.set_xlabel('Channel')
ax1.set_ylabel('Count', color=color)
ax1.bar(result_df['Channel'], result_df['Count'], color=color)
ax1.tick_params(axis='y', labelcolor=color)

# Creating a second y-axis for the line plot
ax2 = ax1.twinx()
color = 'tab:red'
ax2.set_ylabel('Median Lead Score', color=color)
ax2.plot(result_df['Channel'], result_df['Median Lead Score'], color=color, marker='o')
ax2.tick_params(axis='y', labelcolor=color)

# Title
plt.title('Comparison of Counts and Median Lead Score for Each Channel')

# Rotating x-axis labels for better readability
plt.xticks(rotation=45, ha='right')

# Display the plot
plt.show()
</pre>
<samp>
  ![image](https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/5fc8614c-1337-4dcb-800f-b809f7669862)
</samp>
