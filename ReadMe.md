<h1>Database Assignment 3</h1>
<h2>made by Hallur við Neyst and Murched Kayed</h2>
<p>We have completed 4 out of 5 queries, which can be seen down below.</p>

```javascript

//how many twitter users:
{$group: {"_id" : "$user"}},
        {$group:{"_id" : null, "totalAmountOfUsers":{$sum: 1}}}

//most active twitter users (top 10):
{$group:{_id : "$user", number : {$sum : 1}}},
        {$sort : {number: -1}},
        {$limit: 10}

//how many grumpy twitter users (top 5):
{$match: {polarity : 0}},
        {$group: {_id: "$user", polarity : {"$sum" : 1}}},
        {$project : {"user" : 1, "polarity" : 1}},
        {$sort : {polarity: -1}},
        {$limit: 5}
        
 //how many happy twitter users (top 5):
 {$match: {polarity : 4}},
        {$group: {_id: "$user", polarity : {"$sum" : 1}}},
        {$project : {"user" : 1, "polarity" : 1}},
        {$sort : {polarity: -1}},
        {$limit: 5}

//most users who link other twitter users (top 10)
{$match: {text: /@\w*/}},
        {$group: {_id: "$user", number : {"$sum" : 1}}},
        {$sort : {number : -1}},
        {$limit: 10}
        
```

<table>
  <tr>
    <th></th>
    <th>Atomicity</th>
    <th>Sharding</th> 
    <th>Indexes</th>
    <th>Large Number of Collections</th>
    <th>Collection Contains Large Number of Small Documents</th>
          </tr>
 <tr>
    <td>model1</td>
    <td></td> 
    <td></td>
         <td></td>
         <td></td>
         <td></td>

  </tr>
  <tr>
   <td>model2</td>
    <td></td> 
    <td></td>
          <td></td>
          <td></td>
          <td></td>
      
  </tr>
          <tr>
    <td>model3</td>
    <td></td> 
    <td></td>
                  <td></td>
                  <td></td>
                  <td></td>

  </tr>
  </tr>
</table>
