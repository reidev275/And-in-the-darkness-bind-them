- title : And in the darkness bind them: A functional workflow to rule them all
- description : 
- author : Reid Evans
- theme : Simple 
- transition : Fade

***

### And in the darkness bind them
#### A functional workflow to rule them all
####[@ReidNEvans](http://twitter.com/reidnevans)
####http://reidevans.tech
####Founder of [@FunctionalKnox](http://twitter.com/functionalKnox)

***

![Two Towers](images/twotowers.jpg)

***

![Ivory Tower](images/ivorytower.jpg)

***

## What is functional programming?

***

![DomainCodomain](images/domain-codomain.png)

***

### Totality

Every element in the domain must be mapped to some element in the codomain 

***

### Determinism

Calling a function with the same value (in domain) results in same value (in codomain).

***

## Higher Order Functions

***

    [1,2,3].map(x => x * 2);
    // [2,4,6]

***

## Contexts

***

* Promise
* Array
* Task
* Stream
* IO

***

## Algebraic Data Types

***

    type Point = {
      X : double
	  Y : double
    }

    type Shape =
      | Circle of Point * double
      | Poly of Point list

***

```haskell
data Point = Point Double Double

data Shape 
	= Circle Point Double
    | Poly   [Point]
```

***

<section data-background="#5bc0de">

An exception is a kind of cascading goto

**The Pragmatic Programmer**
</section>

***

###[@ReidNEvans](http://twitter.com/reidnevans)

####http://reidevans.tech
####[@FunctionalKnox](http://twitter.com/functionalknox)

