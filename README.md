# useful-arrays
Some useful methods for JavaScript Arrays.

## How to include
You can include this on top of your js code. I appreciate a credit :)

## Random
```js
Array.prototype.random = function(count) {
	if (!count) count = 1;

	let items = this[Math.floor(Math.random() * this.length)];

	if (count > 1) {
		items = [];
		for (let i = 0; i < count; i++) {
			items.push(this[Math.floor(Math.random() * this.length)]);
		}
	}

	return items;
};
```
### Example usage
```js
let arr = ["Banana", "Potato", "Apple", "Orange"];
let twoElements = arr.random(2);
```

## Filter
```js
Array.prototype.filter = function(condition) {
	let arr = [];
	this.forEach(item => {
		if (condition(item) == true) arr.push(item);
	});

	return arr;
};
```

### Example usage
```js
let arr = [
  {name: "Banana", fruit: true}, 
  {name: "Potato", fruit: false}, 
  {name: "Apple", fruit: true}, 
  {name: "Orange", fruit: true}
];
let fruits = arr.filter(item => item.fruit == true);
```

## Get Elements
```js
Array.prototype.getElements = function(element) {
	let returnArr = [];
	this.forEach(item => {
		let el = item[element];
		if (!returnArr.includes(el)) returnArr.push(el);
	});

	return returnArr;
};
```

### Example usage
```js
let arr = [
  {name: "Banana", fruit: true}, 
  {name: "Potato", fruit: false}, 
  {name: "Apple", fruit: true}, 
  {name: "Orange", fruit: true}
];

let names = arr.getElements(name);
```

## Search
```js
Array.prototype.search = function(query) {
	let arr = [];
	this.forEach(item => {
		if (query(item)) arr.push(item);
	});

	return arr;
};
```

### Example Usage
```js
let arr = [
  {name: "Banana", fruit: true}, 
  {name: "Potato", fruit: false}, 
  {name: "Apple", fruit: true}, 
  {name: "Orange", fruit: true}
];

let namesEndingWithE = arr.search(item => item.name.endsWith("e"));
```
