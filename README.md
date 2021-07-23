# homework.call-apply

//Task 1
/*You have an array of user objects, each one has name, surname and id. Write the
function to create another array from it, of objects with id and fullName, where
fullName is generated from name and surname.*/


let john = {name: "John", surname: "Smith", id: 1};
let mary = {name: "Mary", surname: "Key", id: 2};
let users = [john, mary];


let newUsers = users.map(function(user){
	return ({
  	fullname: `${user.name} ${user.surname}`,
  	id: user.id
  })
});



//Task 2
/* Create a decorator decoratorFunction(f, n) that passes the call to f at maximum
once per n milliseconds.
*/


function f(a, b) {
	console.log(a + b)
}


function decoratorFunction(f, ms) {
	let boolean = true;
  
  return function () {
  	if(boolean) {
    	f.apply(this, arguments);
    }
    setTimeout( () => ??, ms)
  }
}

let func = decoratorFunction(f, 1000);

console.log(setTimeout( () => func("a", "b"), 100)); //should print ‘ab’;
console.log(setTimeout( () => func("c", "d"), 1000)); //should be ignored;
console.log(setTimeout( () => func("e", "f"), 1500)); //should print ‘ef;
