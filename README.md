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
  #Plot a bar chart
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
  #Count of unique channels
channel_counts = df['Channel'].value_counts().reset_index()
channel_counts.columns = ['Channel', 'Count']

  #Median lead score for each channel
channel_lead = df.groupby('Channel')['Lead Score'].median().reset_index()
channel_lead.columns = ['Channel', 'Median Lead Score']

  #Merge the two DataFrames on the 'Channel' column
channel_l = pd.merge(channel_counts, channel_lead, on='Channel')

channel_l
</pre>
<samp>
<img width="535" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/d5aefcd6-b1fd-4cfd-9647-3d2d8ace3117">
</samp>
<pre>
  #Plot a bar graph
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
  #Count of unique channels
channel_counts = df['Channel'].value_counts().reset_index()
channel_counts.columns = ['Channel', 'Count']

  #Median lead score for each channel
channel_lead = df.groupby('Channel')['Lead Score'].median().reset_index()
channel_lead.columns = ['Channel', 'Median Lead Score']
channel_lead = channel_lead.sort_values(by='Median Lead Score')

  #Merge the two DataFrames on the 'Channel' column
result_df = pd.merge(channel_counts, channel_lead, on='Channel')

  #Display the combined DataFrame
print(result_df)
</pre>
<samp>
<img width="534" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/b95fefbd-2b20-43bc-8bf3-1979a794dd58">
</samp>
<pre>
  #Larger plot size
fig, ax1 = plt.subplots(figsize=(25, 15))

  #Bar plot for counts
color = 'tab:blue'
ax1.set_xlabel('Channel')
ax1.set_ylabel('Count', color=color)
ax1.bar(result_df['Channel'], result_df['Count'], color=color)
ax1.tick_params(axis='y', labelcolor=color)

  #Creating a second y-axis for the line plot
ax2 = ax1.twinx()
color = 'tab:red'
ax2.set_ylabel('Median Lead Score', color=color)
ax2.plot(result_df['Channel'], result_df['Median Lead Score'], color=color, marker='o')
ax2.tick_params(axis='y', labelcolor=color)

  #Title
plt.title('Comparison of Counts and Median Lead Score for Each Channel')

  #Rotating x-axis labels for better readability
plt.xticks(rotation=45, ha='right')

  #Display the plot
plt.show()
</pre>
<samp>
  <img width="534" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/5fc8614c-1337-4dcb-800f-b809f7669862">
</samp>
<p>
  Number of entities handled by each Sales Owner (Sales Team)
</p>
<pre>
  lead_s = pd.DataFrame(df.groupby('Sales Owner')['Entity Name'].nunique())
lead_s = lead_s.sort_values(by='Entity Name', ascending=False).reset_index()
lead_s
</pre>
<samp>
  <img width="472" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/47cd328b-3631-45d9-a3e5-50a0b23f929b">
</samp>
<pre>
  #Plot the data in a line chart
plt.figure(figsize=(10, 6))
plt.plot(lead_s['Sales Owner'], lead_s['Entity Name'], marker='o', linestyle='-', color='b')
plt.title('Number of Entities per Sales Owner')
plt.xlabel('Sales Owner')
plt.ylabel('Number of Entities')
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.show()
</pre>
<samp>
  <img width="689" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/6e7f2aa7-61be-4d28-a3a7-7e68f2dd6187">
</samp>
<p>
  Current Stage Distribution
</p>
<pre>
  df['Current Stage'].value_counts()
</pre>
<samp>
  <img width="649" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/161aaeb5-476f-452b-aaca-a7ccdf47a4f3">
</samp>
<pre>
  #Plot a horizontal bar chart
ax = df['Current Stage'].value_counts().plot(kind='barh', stacked=True, colormap='viridis', figsize=(10, 6))

  #Add labels and title
ax.set_xlabel('Percentage')
ax.set_ylabel('Current Stage')
ax.set_title('Current Stage Distribution')

  #Display the legend
ax.legend(title='Current Stage', bbox_to_anchor=(1.05, 1), loc='upper left')

  #Show the plot
plt.show()
</pre>
<samp>
<img width="753" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/6f02014c-d2a2-4710-8d06-bff359b551d1">
</samp>
<p>
  <b>
    Conversion Rates at different stages
  </b>
</p>
<p>
  1.Stage = CUSTOMER
</p>
<pre>
  customer_data = df.loc[df['Current Stage'] == 'Customer', ['Current Stage', 'Won Date']]

  #Display the result
print(customer_data.count())
</pre>
<samp>
<img width="536" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/b3b25e69-bf74-456e-a731-2097b62992f4">
</samp>
<pre>
  customer_data['No Won Date'] = customer_data['Won Date'].isnull()
  #Count the occurrences of non-null and null values in 'Won Date'
won_date_counts = customer_data['Won Date'].notnull().value_counts()

  #Plot a pie chart
plt.figure(figsize=(8, 8))
plt.pie(won_date_counts, labels=['Customer', 'Lost'], autopct='%1.1f%%', colors=['lightblue', 'lightcoral'])
plt.title('Distribution of Won Date for Customer Stage=Customer')
plt.show()
</pre>
<samp>
  <img width="642" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/4eea9a3c-9a83-4558-8de8-77757233d54a">
</samp>
<p>
  2.Stage = Proposal
</p>
<pre>
  customer_data1 = df.loc[df['Current Stage'] == 'Proposal', ['Current Stage', 'Won Date']]

  #Display the result
print(customer_data1.count())
</pre>
<samp>
<img width="542" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/dab240ae-930e-4030-91a1-7421037aae80">
</samp>
<pre>
  #Count the occurrences of non-null and null values in 'Won Date'
won_date_count = customer_data1['Won Date'].notnull().value_counts()

  #Plot a pie chart
plt.figure(figsize=(8, 8))
plt.pie(won_date_count, labels=['Lost', 'Customer'], autopct='%1.1f%%', colors=['lightblue','darkblue'])
plt.title('Distribution of Won Date for Customer Stage=Proposal')
plt.show()
</pre>
<samp>
  <img width="620" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/49394bd5-4f2c-47dc-835d-13c73d3d4670">
</samp>
<p>
  3.Stage = QL
</p>
<pre>
  customer_data2 = df.loc[df['Current Stage'] == 'QL', ['Current Stage', 'Won Date']]

  #Display the result
print(customer_data2.count())
</pre>
<samp>
<img width="518" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/58a719a2-69e2-4609-9b59-b6c4b9b9e5ca">
</samp>
<p>
  4.Stage = RQL
</p>
<pre>
  customer_data3 = df.loc[df['Current Stage'] == 'RQL', ['Current Stage', 'Won Date']]

  #Display the result
print(customer_data3.count())
</pre>
<samp>
<img width="518" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/f3d5c165-f2a3-448f-8329-3518cad42b51">
</samp>
<p>
  5.Stage = UQL
</p>
<pre>
  customer_data4 = df.loc[df['Current Stage'] == 'UQL', ['Current Stage', 'Won Date']]

  #Display the result
print(customer_data4.count())
</pre>
<samp>
<img width="518" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/7e5678b1-3fee-4b7b-bcfb-ce9d0294fa31">
</samp>
<p>Lead Response Time</p>
<p>We are finding the difference between QL Creation Date and Prospect Creation Date.</p>
<pre>
  #Select only the relevant columns
df['Date Difference'] = df['QL Creation  Date'] - df['Prospect Creation Date']
df_sorted = df.sort_values(by='Date Difference')
  #Select only the relevant columns
result_df = df_sorted[['Date Difference','Won Date']]
#result_df
  #Select only the relevant columns
result_df = df_sorted[['Date Difference','Won Date']]
result_df.count()
</pre>
<samp>
  <img width="507" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/7ab6b842-b88f-45b9-9b55-1fe7f004317e">
</samp>
<p>
  Assuming here that,
  <ul>
    <li>QL Creation Date on/after Prospect Creation Date, then its NEW entity into the database.</li>
    <li>QL Creation Date before Prospect Creation Date, then its OLD entity from the database.</li>
  </ul>
</p>
<pre>
  #Filter based on Date Difference < 0 and count not null Won Date
negative_difference = df[df['Date Difference'] < pd.Timedelta(0)]
count_not_null_won_date_negative = negative_difference['Won Date'].count()

#Filter based on Date Difference = 0 and count not null Won Date
equal_difference = df[df['Date Difference'] == pd.Timedelta(0)]
count_not_null_won_date_equal = equal_difference['Won Date'].count()

#Filter based on Date Difference > 0 and count not null Won Date
non_negative_difference = df[df['Date Difference'] > pd.Timedelta(0)]
count_not_null_won_date_non_negative = non_negative_difference['Won Date'].count()

#Display the results
print(f"{count_not_null_won_date_negative} number of leads won for OLD Entities/Prospects (where Date Difference < 0)")
print(f"{count_not_null_won_date_equal} number of leads Won for New Entities/Prospects contacted on same day (where Date Difference = 0)")
print(f"{count_not_null_won_date_non_negative} number of leads Won for New Entities/Prospects (where Date Difference > 0)")
</pre>
<samp>
<img width="805" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/4d419896-0ced-41aa-b2ae-8063fa552264">
</samp>
<pre>
  #Circular area plot
categories = ['OLD Entities/Prospects', 'New Entities/Prospects contacted on same day', 'New Entities/Prospects']
counts = [count_not_null_won_date_negative, count_not_null_won_date_equal, count_not_null_won_date_non_negative]

fig, ax = plt.subplots(subplot_kw=dict(aspect="equal"))

wedges, texts, autotexts = ax.pie(counts, autopct='%1.1f%%', textprops=dict(color="w"))

ax.legend(wedges, categories, title="Categories", loc="center left", bbox_to_anchor=(1, 0, 0.5, 1))
plt.setp(autotexts, size=8, weight="bold")

ax.set_title("Count of Leads Won for Prospects/Entites categories")

#Display the plot
plt.show()
</pre>
<samp>
  <img width="667" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/5bed8a6d-ecbd-45f7-8689-08b36cb29a6f">
</samp>
<p>
  For past Nurture entites, number of leads won
</p>
<pre>
  #Count total Won Date when Nurture Date is not null
count_won_date_not_null_nurture = df[df['Nuture Date'].notnull()]['Won Date'].count()

  #Display the result
print("Total Leads Won Date when Nurture Date is not null:", count_won_date_not_null_nurture)
</pre>
<samp>
<img width="565" alt="image" src="https://github.com/anuragprasad95/Sales-Lead-Generation-Analysis/assets/3609255/d6f86133-1c69-4892-92fa-6cc01cc045ff">
</samp>
<p>
  Actionable Insights found
  <ul>
    <li>Top 3 channels from where the 77.21% of the total entities are coming are LinkedIn, Email, Website.
    <li>Top 3 channels for generating Quality Leads are Referral, Cold call, Job Board.</li>
    <li>73.3% of leads converted from the entities having stage = Customers.</li>
    <li>1.6% of leads convereted from entities having stage = Proposals.</li>
    <li>There are negligible changes of converting leads when entities having stage = QL, RQL, UQL.</li>
    <li>48.5% leads converting from new entities/prospects.</li>
    <li>33.33% leads converting from entities/prospects which are contacted on same day through various channels.</li>
    <li>18.20% leads converting from old entities/prospects.</li>
    <li>12.12% leads converted from nurturing entities.</li>
    <li>Restructing Lead Score formula because, leads converted when lead scroe<1 is 32, else its 1 only.</li>
    <li>17 Sales owner had got most entities/propects but rest have few below 10 in numbers.</li>
   </ul>
</p>
