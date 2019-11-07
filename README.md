

Fill out the empty hash that is the value of the `:montague` key. There are four keys in this hash:

* `:patriarch`
* `:matriarch`
* `:hero`
* `:hero_friends`

The first three of these keys point to a value of an empty hash. The fourth key `:hero_friends` has a value of an empty array.

Then, do the same for the empty hash that is the value of the `:capulet` key. This time, your keys are:

* `:patriarch`
* `:matriarch`
* `:heroine`
* `:heroine_friends`

The values are the same as described above. Once you get this test passing, you should have a hash that looks like this:

```ruby
epic_tragedy = {
   :montague => {
      :patriarch => {},
      :matriarch => {},
      :hero => {},
      :hero_friends => []
   },
   :capulet => {
      :patriarch => {},
      :matriarch => {},
      :heroine => {},
      :heroine_friends => []
   }
}

```

Now we're ready to fill out the empty hashes that constitute the values for the `:patriarch`, `:matriarch` and `:hero`/`:heroine` keys, nested inside the family name keys of our epic `epic_tragedy hash`.


### Code Along Challenge III: Character Attributes

According to the diagram that we saw at the very beginning of this exercise, each character has a set of attributes. Matriarch and Patriarchs have a name and an age. The hero and heroine each have a name, age and a status.

In `lib/third_challenge`, you'll find the hash that you built in the previous challenge. Fill out the empty hashes that are the values of the `:patriarch`, `:matriarch`, and `:hero`/`:heroine` keys with the following key/value pairs.

* The Montague `:patriarch` has
  * a `:name` of "Lord Montague" and
  * an `:age` of "53".
* The Montague `:matriarch` has
  * a `:name` of "Lady Montague" and
  * an `:age` of "54".
* The Montague `:hero` has
  * a `:name` of "Romeo",
  * an `:age` of "15", and
  * a `:status` of "alive".
* The Capulet `:patriarch` has
  * a `:name` of "Lord Capulet" and
  * an `:age` of "50".
* The Capulet `:matriarch` has
  * a `:name` of "Lady Capulet" and
  * an `:age` of "51".
* The Capulet `:heroine` has
  * a `:name` of "Juliet",
  * an `:age` of "15", and
  * a `:status` of "alive".

Once you get this test passing, you should have the following hash:

```ruby
epic_tragedy = {
   :montague => {
      :patriarch => {name: "Lord Montague", age: "53"},
      :matriarch => {name: "Lady Montague", age: "54"},
      :hero => {name: "Romeo", age: "15", status: "alive"},
      :hero_friends => []
   },
   :capulet => {
      :patriarch => {name: "Lord Capulet", age: "50"},
      :matriarch => {name: "Lady Capulet", age: "51"},
      :heroine => {name: "Juliet", age: "15", status: "alive"},
      :heroine_friends => []
   }
}

```
We're almost done. Our hero and heroine have two friends each. That constitutes a collection of friends. Since they each have a collection of friends, it makes sense to collect those friends in an array. Since each friend will have his or her own attributes (name, age, etc), our array will be *an array of hashes*!

### Code Along Challenge IV: Nesting Friends and Attributes

The values of the `:hero_friends` and `:heroine_friends` keys currently point to empty arrays. Why arrays? Well, we know that an individual person can be represented by a hash. However, our hero and heroine have multiple friends. So, we need a way to store their friends in list-form. Luckily for us, that's just what arrays are for. Before introducing the concept of hashes, if we told you to make a list of friends what data structure would you reach for? You'd reach for an array!

Fill out these empty arrays with a series of hashes that will contain key/value pairs describing these friends.

The hero's two friends are Benvolio and Mercutio. So, the `:hero_friends` array will contain two hashes. Each of these two hashes have the following three keys:

* `:name`
* `:age`
* `:attitude`

The hero's first friend has

* a name of "Benvolio",
* an age of "17", and
* an attitude of "worried".

The hero's second friend has

* a name of "Mercutio",
* an age of "18", and
* an attitude of "hot-headed".

The heroine's two friends are Steven and Nurse. So, the `:heroine_friends` array will contain two hashes. Each of these two hashes have the following three keys:

* `:name`
* `:age`
* `:attitude`

The heroine's first friend has

* a name of "Steven",
* an age of "30", and
* an attitude of "confused".

The heroine's second friend has

* a name of "Nurse",
* an age of "44", and
* an attitude of "worried".

Once you get this test passing, your hash should look like this:

```ruby
epic_tragedy = {
   :montague => {
      :patriarch => {name: "Lord Montague", age: "53"},
      :matriarch => {name: "Lady Montague", age: "54"},
      :hero => {name: "Romeo", age: "15", status: "alive"},
      :hero_friends => [
         {name: "Benvolio", age: "17", attitude: "worried"},
         {name: "Mercutio", age: "18", attitude: "hot-headed"}
      ]
   },
   :capulet => {
      :patriarch => {name: "Lord Capulet", age: "50"},
      :matriarch => {name: "Lady Capulet", age: "51"},
      :heroine => {name: "Juliet", age: "15", status: "alive"},
      :heroine_friends => [
          {name: "Steven", age: "30", attitude: "confused"},
          {name: "Nurse", age: "44", attitude: "worried"}
      ]
   }
}

```

## Bonus: Manipulating the Hash

In the previous lesson we learned that you can access a value in a hash like this:

```ruby
hash = {first: "first value!", second: "second value!"}

hash[:first]
#  => "first value!"

```

To access the values in our nested hash, we simply tack on additional keys, until we have the last key that points to the value we want to access.

For example, to access the Montague patriarch's name, I use the hash name, `epic_tragedy`, followed by a chained list of all of the key names that precede the value of his name, enclosed in brackets:

```ruby
epic_tragedy[:montague][:patriarch][:name]
#  => "Lord Montague"
```

We can even use this method to change the value of a particular key. If we wanted to reset the Montague patriarch's name to "Michael Jordan", we would do it in the following way:

```ruby
epic_tragedy[:montague][:patriarch][:name] = "Michael Jordan"

puts epic_tragedy

#  =>
{
   :montague => {
      :patriarch => {name: "Michael Jordan", age: "53"},
      :matriarch => {name: "Lady Montague", age: "54"},
      :hero => {name: "Romeo", age: "15", status: "alive"},
      :hero_friends => [
        {name: "Benvolio", age: "17", attitude: "worried"},
        {name: "Mercutio", age: "18", attitude: "hot-headed"}
      ]
   },
   :capulet => {
      :patriarch => {name: "Lord Capulet", age: "50"},
      :matriarch => {name: "Lady Capulet", age: "51"},
      :heroine => {name: "Juliet", age: "15", status: "alive"},
      :heroine_friends => [
        {name: "Steven", age: "30", attitude: "confused"},
        {name: "Nurse", age: "44", attitude: "worried"}
      ]
   }
}
```

### Bonus Code Along Challenge

In `lib/bonus.rb` you'll see our completed `epic_tragedy hash`. We're coming to the end of the epic tragedy of Romeo and Juliet. At this point in the story, Romeo and Juliet are—as in every good tragedy—quite dead. Use the above method to change the status of our hero Romeo and our heroine Juliet from "alive" to "dead". These are bonus and if you're feeling comfortable with Hashes, feel free to move forward. Also, to enable these tests make sure to remove the `x` in front of the `it` block in spec/bonus_spec.rb.

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/building-nested-hashes' title='Code Along Exercise: Building Nested Hashes'>Code Along Exercise: Building Nested Hashes</a> on Learn.co and start learning to code for free.</p>
