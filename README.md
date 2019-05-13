<div>
<h1>Javascript Fundamentals</h1>
<h3>I. Data types</h3>
<p>There are two categories of data in javascript. Primitive values and Reference values. 
</p>
<h6> a. Primitive values</h6>
<ul>
<li>Number</li>
<li>String</li>
<li>Boolean</li>
<li>Symbol</li>
</ul>
All primitive values have the following properties. They are <b>immutable</b> and are <b>passed by copy</b>.
<br>
For example, look at the following code:
<br>
<code>
  let x = 5; // assign the variable x to the primitive value 5
  <br>
  function addfive(num){
  <br>
   num = num + 5;
   <br>
   return num;
   <br>
  } 
  <br>
  addFive(x);  // pass x into addFive
  <br>
  console.log(x)
</code>
<br>
What value is logged to the console in the code above? Our function takes our x variable and returns that variable + 5, but it also assigns the variable to this return value so it is reasonable to assume that our variable x is now equal to 10. However, when you run the code this isn't the case. Why? Because, since x is a primitive, we do not actually pass x into the function. Instead we pass in a copy of the value of x, 5, stored somewhere else in memory. This is called pass by copy!
<h6> b. Reference variables</h6>
<ul>
<li>Arrays</li>
<li>Objects</li>
</ul>
All reference variables have a few important properties. They are <b>mutable</b> and are <b>passed by reference</b>.
<br>
For example, look at the following code:
<br>
<code>
  let x = { myNumber: 5}; // assign the variable x a Reference variable (object)
  <br>
  let y = x; // Make a copy of x
  <br>
  y.myNumber = 10;
  <br>
  console.log(x.myNumber)
</code>
<br>
What value is logged to the console in the code above? We made a copy of our reference variable here then changed the value of myValue in the copy to ten. However, if we console.log x here, we will notice that the value of x.myNumber has also changed to 10. Whys that? This is because when we make a copy of x, we are actually passing a copy of a reference to the object created when we made the x variable.  A reference is like an address, it points to where something is stored in memory. As long as we have this address, we can change/access what is in that location, even if the address is a copy of the original address. What actually happens here is we are making a shallow copy of the variable x, AKA we are copying the address to where x is stored in memory. When we make changes to y, therefore, we are actually making changes to the object that x points to in memory; they point to the same address!. 

<br>
Additionally, if we pass an object into a function, the function will also get a copy of the reference to that object's location in memory. This means that the function has access to all the properties in the original object and can make changes to it unlike with our primitive values!


</div>
<h3>I. Prototypes and Inheritance</h3>
Every object, aka any non-primitive value, in javascript has access to object property called __proto__ (dunder proto) or [[Prototype]] or an internal prototype. This property sets up inheritance in javascript. The internal prototype is a pointer for an object that points to the creator of that object instance. Just like how biological inheritance works, to some degree, the instance or child element inherits the properties of its ancestors, the prototype. For example the array object's [[Prototype]] is the Object object. This is why arrays have access to all the methods that an object has access to, because Object is the parent/prototype of Array. This however extends even further. An object's prototype can have its very own prototype. If this is the case, the object has access to the properties and methods stored in its own prototype and its prototype's prototype!   
