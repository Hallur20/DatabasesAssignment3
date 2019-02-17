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

The results were these:

totalAmountOfUsers: 659774

most active twitter users:

Username: lost_dog Tweets: 549
Username: webwoke Tweets: 345
Username: tweetpet Tweets: 310
Username: SallytheShizzle Tweets: 281
Username: VioletsCRUK Tweets: 279
Username: mcraddictal Tweets: 276
Username: tsarnick Tweets: 248
Username: what_bugs_u Tweets: 246
Username: Karen230683 Tweets: 238
Username: DarkPiano Tweets: 236

most grumpy and happy users:

Negative list:
Username: lost_dog Tweets: 549
Username: tweetpet Tweets: 310
Username: webwoke Tweets: 264
Username: mcraddictal Tweets: 210
Username: wowlew Tweets: 210
Positive list:
Username: what_bugs_u Tweets: 246
Username: DarkPiano Tweets: 231
Username: VioletsCRUK Tweets: 218
Username: tsarnick Tweets: 212
Username: keza34 Tweets: 211

users who link the most:
Username: lost_dog Links: 549
Username: tweetpet Links: 310
Username: VioletsCRUK Links: 251
Username: what_bugs_u Links: 246
Username: tsarnick Links: 245
Username: SallytheShizzle Links: 229
Username: mcraddictal Links: 217
Username: Karen230683 Links: 216
Username: keza34 Links: 211
Username: DarkPiano Links: 202

<table>
  <tr>
    <th>Model</th>
    <th>Atomicity</th>
    <th>Sharding</th> 
    <th>Indexes</th>
    <th>Large Number of Collections</th>
    <th>Collection Contains Large Number of Small Documents</th>
          </tr>
 <tr>
    <td>Arrays of Ancestors</td>
    <td>x</td> 
    <td>x</td>
         <td>x</td>
         <td></td>
         <td>x</td>

  </tr>
  <tr>
   <td>Materialized paths</td>
    <td>x</td> 
    <td>x</td>
          <td>x</td>
          <td></td>
          <td>x</td>
      
  </tr>
          <tr>
    <td>Nested Sets</td>
    <td>x</td> 
    <td></td>
                  <td></td>
                  <td>x</td>
                  <td></td>

  </tr>
  </tr>
</table>
