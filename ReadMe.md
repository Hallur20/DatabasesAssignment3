<h1>Database Assignment 3</h1>
<h2>made by Hallur við Neyst and Murched Kayed</h2>
<h2>1. Twitter data</h2>
<p>We have completed 4 out of 5 queries, which can be seen down below. The problem with the 5th query was that we did not manage to
 obtain the users who were mentioned in the text. 
</p>

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

<p>most active twitter users:</p>
<p>
Username: lost_dog Tweets: 549<br>
Username: webwoke Tweets: 345<br>
Username: tweetpet Tweets: 310<br>
Username: SallytheShizzle Tweets: 281<br>
Username: VioletsCRUK Tweets: 279<br>
Username: mcraddictal Tweets: 276<br>
Username: tsarnick Tweets: 248<br>
Username: what_bugs_u Tweets: 246<br>
Username: Karen230683 Tweets: 238<br>
Username: DarkPiano Tweets: 236</p>

<p>most grumpy and happy users:</p>

<p>Negative list:
Username: lost_dog Tweets: 549<br>
Username: tweetpet Tweets: 310<br>
Username: webwoke Tweets: 264<br>
Username: mcraddictal Tweets: 210<br>
Username: wowlew Tweets: 210<br>
Positive list:
Username: what_bugs_u Tweets: 246<br>
Username: DarkPiano Tweets: 231<br>
Username: VioletsCRUK Tweets: 218<br>
Username: tsarnick Tweets: 212<br>
Username: keza34 Tweets: 211</p>

<p>users who link the most:</p><p>
Username: lost_dog Links: 549<br>
Username: tweetpet Links: 310<br>
Username: VioletsCRUK Links: 251<br>
Username: what_bugs_u Links: 246<br>
Username: tsarnick Links: 245<br>
Username: SallytheShizzle Links: 229<br>
Username: mcraddictal Links: 217<br>
Username: Karen230683 Links: 216<br>
Username: keza34 Links: 211<br>
Username: DarkPiano Links: 202</p>
<h2>2. Modelling</h2>
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
<h2>Factors</h2>
 <h3>Atomicty</h3>
<p>Atomicity is part of the ACID model (Atomicity, Consistency, Isolation, Durability), It is an atomic transaction of database operations, which mean that either everything should happen a time, or nothing happens. Atomic implies indivisibility and irreducibility.
Transactions are often composed of multiple statements. Atomicity guarantees that each transaction is treated as a single "unit", which either succeeds completely, or fails completely, if one of the statements fails the whole transaction fail as well.
A good example, a bank's software may implement a transfer from account A to account B as a withdrawal from A followed by a deposit to B. If the first action happens, then the second had better happen as well.
Another example, in an online airline-booking system, a booking may consist of 2 separate actions that together form a transaction -- paying for the seat and reserving the seat for the customer who’s just paid. Business logic dictates that these two, though distinct and separate actions, must occur together. If one happens without the other, problems can occur. For example, the system may reserve the same seat for two separate customers.</p>
<h3>Sharding</h3>
<p>Sharding is used to separate very big database into smaller, faster, more easily managed horizontal partitioning databases. Shard means a small part of a whole.
A good example is splitting a customer database geographically. Customers located on the East Coast can be placed on one server, while customers on the West Coast can be placed on a second server. Assuming there are no customers with multiple locations, the split is easy to maintain and build rules around.
In some cases, sharding a database that holds less structured data can be a complex process, and the resulting shards (databases) may be difficult to maintain.</p>



<h2>brief arguments</h2>
<p>we agreed that atomicity is important in all the 3 models, because of the fact that the depended steps have to happen at the same time, or else it will fail. Sharding made sense in ancestors/materialized because they are able to being split into smaller databases, while nested sets is more vulnarable because it wants to be static. Indexes works well with ancestors/materialized because of the index being able to act as a foreign key in other collections. We believe that a large number of collections would work well with nested sets because of the fact that is not much desire for storing tree nodes in the model. A collection with many documents works better for materialized/ancestors because they are more open for modification </p>

<p>we were not sure if the project was supposed to be included but if u need it to work type npm install in gitbash and remove comments etc...</p>

<p>link for github: https://github.com/Hallur20/DatabasesAssignment3/edit/master/ReadMe.md</p>
