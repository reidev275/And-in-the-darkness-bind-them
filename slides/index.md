- title : And in the darkness bind them: A functional workflow to rule them all
- description : 
- author : Reid Evans
- theme : Simple 
- transition : Fade

***

### And in the darkness bind them
#### A functional workflow to rule them all
#### [@ReidNEvans](http://twitter.com/reidnevans)
#### http://reidevans.tech
#### Founder of [@FunctionalKnox](http://twitter.com/functionalKnox)

***

![Two Towers](images/twotowers.jpg)

***

![Ivory Tower](images/ivorytower.jpg)

***

##1 data type
## +
##3 functions

***

All your wildest dreams will come true

![Napoleon](images/napoleon.gif)

***



***

***

## What is functional programming?

***

![DomainCodomain](images/domain-codomain.png)

***

## Totality

Every element in the domain must be mapped to some element in the codomain 

***

## Determinism

Calling a function with the  same value (in domain) results in same value (in codomain).

***
F#

	let double x = x * 2
	
---
Javascript

	[lang=js]
	function greet(who) {
		console.log("hello " + who)
	}

---
F#

	let formatDate format =
		DateTime.Now.ToString(format)

---
C#

	[lang=cs]
	public string FormatDate(DateTime date, string format)
	{
		return date.ToString(format);
	}

---
F#

	let divide x y = x / y
	
---
F#

	let divide x y =
		if y = 0
		then None
		else Some (x / y)

---
Haskell


	[lang=haskell]
	head [1,2,3]
	1

---
Haskell

        head []
        *** Exception: Prelude.head: empty list
***

## Higher Order Functions

Functions that accept or return another function

***

![eyeroll](images/eyeroll.gif)

***

	[lang=javascript]
	var list = [1,2,3,4],
        result = [];
		
	for (var i = 0; i < list.length; i++) {
		if (list[i] % 2 === 0) {
			result.push(list[i] * 2);
		}
	}

---

	[lang=javascript]
    [1,2,3,4].filter(x => x % 2 == 0)
             .map(x => x * 2)
			 
---

	[lang=javascript]
	const isEven = x => x % 2 == 0,
          timesTwo = x => x * 2;
		
	[1,2,3,4].filter(isEven)
             .map(timesTwo)
			 
---

	[lang=javascript]
    const isEven = x => x % 2 == 0,
          timesTwo = x => x * 2;

    [1,2,3,4].filter(isEven)
             .map(timesTwo)

	timesTwo(2)
	
	$.when(2)
	.then(timesTwo)
***

	[lang=javascript]
	const isAdmin = x => x.level > 9 && x.isActive;
	
	function getAdmins() {
		return $.getJson('/api/users')
				.done(data => data.filter(isAdmin))
	}


***


## Algebraic Data Types

***

Product Type

      type Point = {
          X : double
          Y : double
      }

Sum Type

      type Shape =
        | Circle of Point * double
        | Polygon of Point list

***

## The One Type

---

Haskell

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

Swift

	[lang=cs]
	enum Either<T1, T2> {
		case Left(T1)
		case Right(T2)
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

PHP

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

## Three types of functions

---

1. Functions that don't know about our type


	let add x y = x + y
	
	add 2 3
	5

---
 
2. Functions that return our type 


	// 'a list -> Either<String, 'a>
    let head = function
        | [] -> Left "Cannot take head an of empty list"
        | x::_ -> Right x
		
	head []
	Left "Cannot take head of an empty list"
	
	head [1;2;3]
	Right 1

---

3. Functions that interop with impure libraries


	// string -> string*
    File.ReadAllText path

***

## Putting it all together

---

	let createLocation =
		//geocode location
		//format address
		//insert into db
		//return location

---
	let urlBase = 
		"https://maps.googleapis.com/maps/api/geocode/json?address="

	let geocodeLocation x =
		let response = 
			urlBase + x.Address + "," + x.Zip
			|> Geocoder.load
		let loc = (response.results |> Seq.head).geometry.location
		{ x with Lat = loc.lat; Long = loc.lng }
		
---


***

Node

    [lang=js]
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

### [@ReidNEvans](http://twitter.com/reidnevans)

#### http://reidevans.tech
#### [@FunctionalKnox](http://twitter.com/functionalknox)
