Download Link: https://assignmentchef.com/product/solved-comp250-finl-project
<br>
For this project you will write several classes to simulate searching through a Twitter-like data base. Make sure you implement all required methods according to the instructions given below. In addition to the required methods, you are free to add as many other <strong>private </strong>methods as you want. Note that null keys are not allowed in the hash table. Remember that in most of scenarios objects comparison does not use ‘==’. We highly suggest you read through the entire instructions before you start coding. You do not necessarily have to implement the methods in the order in which they are presented. Note also that this project is meant for you to practice first hand how to implement a hash table as well as learning when to use it and how to exploit its properties. For this project you want to focus on optimizing the time efficiency of your code. We do not care about space efficiency. Enjoy coding this last project!

The class MyHashTable has the following fields:

<ul>

 <li>An int for the number of entries stored inside the table.</li>

 <li>An int for the number of buckets the table has (Note that this value is initialized by the constructor, but could change later on if the number of entries increases).</li>

 <li>A final double representing the maximum load factor for the hash table.</li>

 <li>An ArrayList of buckets used to store the entries to the table. Where each bucket is a LinkedList of HashPairs.</li>

</ul>

Implement the following public methods in the MyHashTable class:

<ul>

 <li>The constructor MyHashTable() which takes an int as input representing the initial capacity of the table.<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> Using the input, the constructor initializes all the fields.</li>

 <li>A put() method that takes a <em>key </em>and a <em>value </em>as input. The method adds a HashPair of the <em>key </em>and <em>value </em>to the hash table. If a HashPair with the <em>key </em>already exists in the hash table, then you should overwrite the old <em>value </em>associated with the <em>key </em>with the new one. This method should be <em>O</em>(1) on average. If in this hash table there was a previous value associated to the given key, then the method overwrites it with the new value and returns the old one. If there was no value associated to the given key, then the method returns null. Remember that the load factor of the table should never be greater than the maximum load factor stored in the appropriate field.</li>

 <li>A get() method which takes a <em>key </em>as input and returns the <em>value </em>associated with it. If there is no such key in the hash table, then the method should return null. This method should run in <em>O</em>(1) on average.</li>

 <li>A remove() method that takes a <em>key </em>as input and removes from the table the entry (i.e. the HashPair) associated to this <em>key</em>. The method should return the <em>value </em>associated to the <em>key</em>. If the <em>key </em>is not found, then the method returns null. This method should run in <em>O</em>(1) on average.</li>

 <li>A rehash() method which takes no input and modifies the table so that it contains double the number of buckets. This method should be <em>O</em>(<em>m</em>) where <em>m </em>is the number of buckets in the table.<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a></li>

 <li>A keys() method which takes no input and returns an ArrayList containing all the keys in the table. The keys in the returned ArrayList may be in any order. This method should be <em>O</em>(<em>m</em>) where <em>m </em>is the number of buckets in the table.</li>

 <li>A values() method which takes no input and returns an ArrayList containing all the <em>unique </em>values in the table. The returned ArrayList of <em>unique </em>values may be in any order. This method should be <em>O</em>(<em>m</em>) where <em>m </em>is the number of buckets in the table.</li>

</ul>

Notice that inside this class you can also see two static methods. The method called slowSort() is already implemented. It takes as input an object of type MyHashTable where the values are Comparable. The method returns an ArrayList containing all the keys in the table, sorted in descending order based on the values they map to. The time complexity of slowSort is <em>O</em>(<em>n</em><sup>2</sup>), where <em>n </em>is the number of pairs in the table. Your should implement:

<ul>

 <li>a method called fastSort which performs the same task as slowSort but with a time complexity of <em>O</em>(<em>n </em> log(<em>n</em>)). It is up to you to decide which sorting algorithm you’d like to implement.</li>

</ul>

Finally, implement the following methods from the private nested class MyHashIterator:

<ul>

 <li>The constructor which should be <em>O</em>(<em>m</em>), where <em>m </em>is the number of buckets in the table.</li>

 <li>A hasNext() method which should be <em>O</em>(1) and returns true if the hash table has a next HashPair.</li>

 <li>A next() method which is also <em>O</em>(1) and returns the next HashPair.</li>

</ul>

Implement the following public methods inside the Twitter class. Note that you are allowed to add as many private methods and fields as you see fit.

<ul>

 <li>The constructor Twitter() which takes as input an ArrayList of Tweets and an ArrayList of Strings denoting the stop words. A stop word is a commonly used word that is ignored by search engines. We suggest you first look at what you need to implement in the rest of the class, before deciding how to implement the constructor. The time complexity of this method should be <em>O</em>(<em>n</em>+<em>m</em>) where <em>n </em>is the number of tweets and <em>m </em>is the number of stop words.</li>

 <li>A method addTweet() which takes a Tweet as input and adds it to the Twitter. This method should be <em>O</em>(1).</li>

 <li>A method latestTweetByAuthor() which takes a String as input and returns the latest Tweet the given author has posted. If the author has not posted any tweet, then the method returns null. This method should be <em>O</em>(1).</li>

 <li>A method tweetsByDate() which takes a String as input representing a date in this format YYYY-MM-DD. The method returns an ArrayList of Tweets containing all the tweets posted on that given date. If there are no tweets on the given date, then the method returns null. This method should be <em>O</em>(1).</li>

 <li>A method trendingTopics() which takes no input and returns an ArrayList of Strings containing all the words (which are not stop words!) that appear in all the tweets of this Twitter. The words should be ordered from most frequent to least frequent by counting in how many tweet messages the words appear. Note that if a word appears more than once in the same tweet, it should be counted only once. <strong>This method should be </strong><em>O</em>(<em>n</em>∗<em>log</em>(<em>n</em>)) <strong>where </strong><em>n </em><strong>is the number of tweets. Note that the idea here is that the method would build a hash table in </strong><em>O</em>(<em>n</em>)<strong>, and then call the </strong>fastSort <strong>from the </strong>MyHashTable <strong>class which runs in </strong><em>O</em>(<em>n </em>∗ <em>log</em>(<em>n</em>)). Note that tweet messages have a limit on the number of words, so iterating through the words in a message increases the time complexity of the method by a constant. <strong>More over this implies that the number of unique words in a set of tweets is bounded by the number of tweets times a constant, which means that the function that describes the maximum number of unique words in </strong><em>n </em><strong>tweets is </strong><em>O</em>(<em>n</em>)<strong>. </strong>Here a couple of hints:</li>

 <li>You can find in the template an helper method called getWords which you can use to extract an array list of words out of a message. Note that the method separate the words based on apostrophes and space characters. Characters that are not letters from the English alphabet are ignored. So, for instance ”@pple!” becomes ”pple” and ”user521dg” becomes ”userdg”.</li>

 <li>When comparing strings make sure to ignore the case of the characters. You want to be sure for instance not to miss stop words typed in either upper or lower case. Words like ”HELP”, ”Help”, ”help”, and ”hElP” should all be considered as the same word.</li>

</ul>

If you test trendingTopics with an object of type Twitter created with the list of tweets from the HashTableTester.java and an empty list as stop words, then these are the top four trending words: “spirit” with 16 occurrence, “a” with 15 occurrences, “that” with 8 occurrences, and “time” with 7 occurrences

<a href="#_ftnref1" name="_ftn1">[1]</a> The capacity is the number of buckets in the hash table, and the initial capacity is simply the capacity at the time the hash table is created.

<a href="#_ftnref2" name="_ftn2">[2]</a> In the slides we mention that these methods run in <em>O</em>(<em>n </em>+ <em>m</em>) where <em>n </em>is the number of entries, and <em>m </em>is the number of buckets. Note that if you have a good hash function and a max load factor of 0.75, then this is equivalent to say that the method runs in <em>O</em>(<em>m</em>).