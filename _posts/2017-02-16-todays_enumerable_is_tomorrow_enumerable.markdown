---
layout: post
title:  "**Today's Enumerable is tomorrow Enumerable**"
date:   2017-02-16 01:39:54 -0500
---

Ruby offers various enumerable methods. For my first technical blog post, I decided to explore them. As we have been ```enlightened```  by our great Flatiron instructors, we now know that if you happen to be using an ```.each``` method, chances are you are using the wrong method. 

Knowing this, I decided I needed to spend more time exploring the Ruby documentation for interesting array & hash methods to gain a better understanding of all the great tools at our disposal. Today, I go over a few methods that I believe will be very useful.


# ```.fetch```
Working with databases this past week in class, ```.fetch``` has been useful more than once. I wanted to point it out and give some more examples on its use and syntax before moving on to other methods.

The Method . fetch attempts to return the element at a specific ```index```. 
It returns an Error(IndexError) is the reference is outside the array bounds.
```
test = ["a","b","c","d","e"]         array.length = 5
 => ["a", "b", "c", "d", "e"] 
test.fetch(0) => “a” 
test.fetch(1) => "b" 
test.fetch(2) => "c" 
test.fetch(4) => "e" 
test.fetch(5)=>
		IndexError: index 5 outside of array bounds: -5...5 
			from (irb):95:in `fetch' 
			from (irb):95 from /Users/firstlast/.rvm/rubies/ruby-2.4.0/bin/irb:11:in 
		`<main>'

test.fetch(-1) => return the last element
```

It also allow you to customize the ```return``` by passing it a block. see example below:

```
test.fetch(8){ |x| puts "Nope! not today, value at index #{x} is out of boudries" } 
#=>
 Nope! not today, value at index 8 is out of boudries 
=> nil
```




# ```.group_by```

I found that ```.group_by``` method was very interesting because it allows the user to group values in a new hash. 

This functionality can easily implemented as a way to separate elements from an array (i.e, last names, doubles, account number, duplicates) that would meet a condition. It then allows you to access the values of the two branches of that new returned hash.
```
names.group_by{|name| name.length == 5} 
#=> {
		false=>["Albertine", "Modesto", "Sherwood", "Alexandra", "Flavia", "William", "Rozella", "Albertine"], 
		true=>["Romeo", "Jules", "Clara"]
	}

names = %w{Albertine Romeo Jules Modesto Sherwood Alexandra Flavia Clara William Rozella}
	#=> ["Albertine", "Romeo", "Jules", "Modesto", "Sherwood", "Alexandra", "Flavia", "Clara", "William", "Rozella"]

names.group_by { | name | name.length >5 } 
	# => {	
		true=>["Albertine", "Modesto", "Sherwood", "Alexandra", "Flavia", "William", "Rozella"], 
		false=>["Romeo", "Jules", "Clara"]
		}

names.group_by{ |name| name == "Albertine"} 
#=>
	{ 
	true=>["Albertine", "Albertine"], 
	false=>["Romeo", "Jules", "Modesto", "Sherwood", "Alexandra", "Flavia", "Clara", "William", "Rozella"]
	}
```




# ```.cycle```  

The ```.cycle``` method implements the given block  for each element n times or forever if nil is given. It does nothing if a non-positive number is given or the array is empty. It would return nil if the loop has finished without getting interrupted. 

In this example I created a array and empty array to store the elements that will pass my test:
```
names = ["Albertine", "Romeo", "Jules", "Modesto", "Sherwood", "Alexandra", "Flavia", "Clara", "William", "Rozella"]
names2 = [ ]   

names.cycle(1){ |x| names2 <<  "#{x} plus one“ } 
#=> ["Albertine plus one", "Romeo plus one", "Jules plus one", "Modesto plus one", "Sherwood plus one", "Alexandra plus one", 
		"Flavia plus one", "Clara plus one", "William plus one", "Rozella plus one"]

names.cycle(1){|x| new_arr<<"#{x} was picked" if x.length == 5 }
	#=> Nil
#=> new_arr
# => ["Romeo was picked", "Jules was picked", "Clara was picked"]

names.cycle(2){|x| new_arr<<"#{x} was picked" if x.length == 5 } 
=> nil 

new_arr 
=> ["Romeo was picked", "Jules was picked", "Clara was picked", "Romeo was picked", "Jules was picked", "Clara was picked"]
```


This method is useful for two reasons. First,``` .cycle ```can be run as many times as the coder wants. ```.cycle()``` takes in an argument ```(x)``` as an indicator to how many cycles the coder wants this method to run. ```.cycle ```with no argument create a infinite loop. 
Secondly, the fact that ```.cycle``` does not alter the original array can be a saver. This would require you to code in the passing of the argument to a storing array (i.e: ```new_arr<< x ```) within the block.


Cycle allow you to pass in an argument ``x`` where``x`` is the number of cycles that that will iterate over an object or an array.
example:
```
 arr = ["Arthur", "b", "c", "d"] 

 arr.cycle(1){|x| new_arr << x if x.length>4}
 => nil 

new_arr => ["Arthur"] 
```

# ```.rotate``` 

The method returns a new array by rotating the array so that the element at index passed as ```cycle(index)``` is the first element of the new array. If ```X``` is negative then it rotates in the opposite direction.
This method acts in a similar manner than``` .reserve``` but the integer argument can be passed in that affects the center of rotation makes this a more powerful method.

Visually is give this:

```
test = [1,2,"x","y"]

test.rotate(1)	=> [2, "x", "y", 1]
test.rotate(2)	=> ["x", "y", 1, 2] 
test.rotate(3) 	=> ["y", 1, 2, "x"] 
test.rotate(4) 	=> [1, 2, "x", "y"] 
test.rotate(5) 	=> [2, "x", "y", 1]
test.rotate(6) 	=> ["x", "y", 1, 2]
test.rotate(7) 	=> ["y", 1, 2, "x"]
test.rotate(8) 	=> [1, 2, "x", "y"]
test.rotate(9) 	=> [2, "x", "y", 1]
test.rotate(-1) 	=> ["y", 1, 2, "x"]

test = [1,2,3,"x","y","z"] 
#=> [1, 2, 3, "x", "y", "z"] 

test.rotate(1) => [2, 3, "x", "y", "z", 1] = test.rotate(7) => [2, 3, "x", "y", "z", 1]
test.rotate(2) => [3, "x", "y", "z", 1, 2] = test.rotate(8) => [3, "x", "y", "z", 1, 2]
test.rotate(3) => ["x", "y", "z", 1, 2, 3]
test.rotate(4) => ["y", "z", 1, 2, 3, “x”] =  test.rotate(10) => ["y", "z", 1, 2, 3, "x"] = test.rotate(-2) => ["y", "z", 1, 2, 3, "x"] 
test.rotate(5) => ["z", 1, 2, 3, "x", "y"] = test.rotate(-1) => ["z", 1, 2, 3, "x", "y"]
test.rotate(6) => [1, 2, 3, "x", "y", "z"]
```

- - - - - - - - - - - -

I will let your imagination loop on all the infinite possible uses of these methods in your future prorgrams. 
