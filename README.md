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
