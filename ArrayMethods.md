#Array methods [every(),filter(),map(),some(),forEach()]


*key = v，val = i，array	= array
*以下均为构造函数。
##every()
every 仅仅只返回true或false
var a = [1, 2, 3, 4, 5 ,6],
b = a.every(function(item, index, array){
        return item;
});
console.log(b);//true


##filter()
filter根据判断true或false来返回一个新的数组
var a = [1, 2, 3, 3, null, 5 ,6,'richardgong', undefined],
b = a.filter(function(item, index, array){
        return index;
});
console.log(b);// [2, 3, 3, null, 5, 6, "richardgong", undefined] 

##forEach()
forEach只遍历数组，但不返回任何值。
var a = [1, 2, 3, 3, null, 5 ,6,'richardgong', undefined],
b = a.forEach(function(k, v, arr){
        console.log('K:',k, "v:", v, "arr:",arr);
});
console.log("b:", b);//K: 1 v: 0 arr: [1, 2, 3, 3, null, 5, 6, "richardgong", undefined] b.js:3
K: 2 v: 1 arr: [1, 2, 3, 3, null, 5, 6, "richardgong", undefined] b.js:3
K: 3 v: 2 arr: [1, 2, 3, 3, null, 5, 6, "richardgong", undefined] b.js:3
K: 3 v: 3 arr: [1, 2, 3, 3, null, 5, 6, "richardgong", undefined] b.js:3
K: null v: 4 arr: [1, 2, 3, 3, null, 5, 6, "richardgong", undefined] b.js:3
K: 5 v: 5 arr: [1, 2, 3, 3, null, 5, 6, "richardgong", undefined] b.js:3
K: 6 v: 6 arr: [1, 2, 3, 3, null, 5, 6, "richardgong", undefined] b.js:3
K: richardgong v: 7 arr: [1, 2, 3, 3, null, 5, 6, "richardgong", undefined] b.js:3
K: undefined v: 8 arr: [1, 2, 3, 3, null, 5, 6, "richardgong", undefined] b.js:3
b: undefined;

##map()
返回遍历后的任意值，每个item对应一个值。
var a = [1, 2, 3, 3, null, 5 ,6,'richardgong', undefined],
b = a.map(function(key, val, array){
        return key +'richardgong';
    });
console.log(b);//["1richardgong", "2richardgong", "3richardgong", "3richardgong", "nullrichardgong", "5richardgong", "6richardgong", "richardgongrichardgong", "undefinedrichardgong"]

##some()
some只返回true或false，遍历数组所有，如果其中一个返回true则true，不然则false。
