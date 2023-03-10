# Object.seal

var obj = { foo: 'foo', bar: function () { return 'bar'; } };
Object.seal(obj)
obj.newFoo = 'newFoo';
obj.bar = function () { return 'foo' };
obj.newFoo; // undefined
obj.bar(); // 'foo'
// Can't make foo an accessor property
Object.defineProperty(obj, 'foo', {
 get: function () { return 'newFoo'; }
}); // TypeError
// But you can make it read only
Object.defineProperty(obj, 'foo', {
writable: false
}); // TypeError
obj.foo = 'newFoo';
obj.foo; // 'foo';
In strict mode these operations will throw a TypeError
(function () {
 'use strict';
 var obj = { foo: 'foo' };
 Object.seal(obj);
 obj.newFoo = 'newFoo'; // TypeError
}());
