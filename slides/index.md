- title : And in the darkness bind them: A functional workflow to rule them all
- description : 
- author : Reid Evans
- theme : Simple 
- transition : Fade

***

## And in the darkness bind them
### A functional workflow to rule them all
### [@ReidNEvans](http://twitter.com/reidnevans)
### http://reidevans.tech
### Founder of [@FunctionalKnox](http://twitter.com/functionalKnox)

***

![Two Towers](images/twotowers.jpg)

***

![Ivory Tower](images/ivorytower.jpg)

***

## The Pitch

1 data type
3 functions

***

All your wildest dreams will come true

![Napoleon](napoleon.gif)

***

* Functional Programming
* Higher Order Functions
* Algebraic Data Types
* Two types of functions
* Putting it all together

*** 

## What is functional programming?

***

![DomainCodomain](images/domain-codomain.png)

***

## Totality

Every element in the domain must be mapped to some element in the codomain 

***

### Determinism

Calling a function with the  same value (in domain) results in same value (in codomain).

***

# TODO: show they can be written in many languages.

---


Javascript

	[lang=js]
	function greet(person) {
		return 'Hello, ' + person;
	}
	
***

Haskell

	[lang=haskell]
	head [1,2,3]
	

***

## Higher Order Functions

Functions that accept or return another function

***
	[lang=javascript]
	var list = [1,2,3,4],
		result = [];
		
	for (var i = 0; i < list.length; i++) {
		if (list[i] % 2 === 0) {
			result.push(list[i] * 2);
		}
	}

***
	[lang=javascript]
    [1,2,3,4].filter(x => x % 2 == 0)
			 .map(x => x * 2)
			 
***
	[lang=javascript]
	const isEven = x => x % 2 == 0,
		  timesTwo = x => x * 2;
		
	[1,2,3,4].filter(isEven)
			 .map(timesTwo)
			 
	timesTwo(2)
	
	$.when(2)
	.then(timesTwo)
	
***


## Algebraic Data Types

***

F#

    type Point = {
      X : double
	  Y : double
    }

    type Shape =
      | Circle of Point * double
      | Polygon of Point list

Haskell

	[lang=haskell]
	type Point = (Double,Double)

	data Shape 
		= Circle  Point Double
		| Polygon [Point]

***


## Contexts

* Promise
* Array
* Task
* Stream
* IO

***

## The One Type

	[lang=haskell]
	data Either a b
		= Left a
		| Right b

---

F#

	type Either<'Left, 'Right> =
		| Left of 'Left
		| Right of 'Right		
		
---

C#
	
	[lang=cs]
	class Either<Right, Left>
	{
	  readonly Right right;
	  readonly Left left;
	  readonly bool isRight = true;

	  public Either(Right val)
	  {
		right = val;    
	  }

	  public Either(Left val)
	  {
		left = val;
		isRight = false;
	  }
	}


---

Python

	[lang=py]
	class Either(object):
	   def __init__(self, value, is_right):
		 self.is_right = is_right
		 self.value = value

	   @staticmethod
	   def right(value):
		 return Either(value, True)

	   @staticmethod
	   def left(value):
		 return Either(value, False)	
	
---

	[lang=php]
	<?php
	class Either {
	  private $val = null;
	  private $isRight = TRUE;
	  private function __construct( $val, $isRight ) {
		$this->val = $val;
		$this->isRight = $isRight;
	  }
	  public static function Right( $right ) {
		$instance = new self( $right, TRUE );
		return $instance;
	  }
	  public static function Left( $left ) {
		$instance = new self( $left, FALSE );
		return $instance;
	  }
	}
	?>  
	
***

What's so important about this type?

***	

Node

	[lang=js]
	//                        left    right
	//                          \      /
	fs.readFile('/etc/passwd', (err, data) => {
	  if (err) throw err;
	  console.log(data);
	});

Elixir

	[lang=ruby]
	File.read("hello.txt")
	# {:ok, "World"}
	
	File.read("invalid.txt")
	# {:error, :enoent}

***

	[lang=cs]
	File.ReadAllText("invalid.txt")
	// FileNotFoundException

***

<section data-background="#5bc0de">

"An exception is a kind of cascading goto"

**The Pragmatic Programmer**
</section>

***

## Two types of functions

*** 

Functions that don't know about our type

    let add x y = x +y

***
 
Functions that return our type 

    let head = function
        | [] -> Left "Cannot take head of empty list"
        | [x:_] -> Right x
        
***

### [@ReidNEvans](http://twitter.com/reidnevans)

#### http://reidevans.tech
#### [@FunctionalKnox](http://twitter.com/functionalknox)

