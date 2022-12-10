<h1>Week 4 Assignment </h1>
Problem 1: Recursion
Write a recursive function called flatTheArray which accepts an array of arrays 
and returns a new array with all values flattened.

flatTheArray([1, 2, 3, [4, 5] ]) // [1, 2, 3, 4, 5] <br>
flatTheArray([1, [2, [3, 4], [[5]]]]) // [1, 2, 3, 4, 5]<br>
flatTheArray([[1],[2],[3]]) // [1,2,3]<br>
flatTheArray([[[[1], [[[2]]], [[[[[[[3]]]]]]]]]]) // [1,2,3]<br>


    const flatTheArray = (arr) => {
    let newArray = []
    arr.forEach(data => {
        if (Array.isArray(data)) {
            newArray.push(...flatTheArray(data))
        } else {
            newArray.push(data)
        }
    })
    return newArray
    }
    console.log(flatTheArray([1, 2, 3, [4, 5]]))
    console.log(flatTheArray([1, [2, [3, 4], [[5]]]]))
    console.log(flatTheArray(([[1], [2], [3]])))
    console.log(flatTheArray([[[[1], [[[2]]], [[[[[[[3]]]]]]]]]]))


Problem 2: Recursion
Write a recursive function called capitalizeWords. 
Given an array of words, return a new array containing each word capitalized.<br>
let words = ['tony', 'kim'];<br>
capitalizedAllLetters(words); // ['TONY', 'KIM']<br>

    const capitalizeAllLetters = (array) => {
    if (array.length === 1) {
        return [array[0].toUpperCase()]
    }
    let data = capitalizeAllLetters(array.slice(0, -1))

    data.push(array.slice(array.length - 1)[0].toUpperCase())
    
    return data

    }

    console.log(capitalizeAllLetters(['tony', 'kim', 'james', 'kyan']))

Problem 3: Recursion 
example 7: factorial

factorial(1) // 1
factorial(2) // 2
factorial(7) // 5040

Write a function factorial which accepts a number and returns the factorial of that number.
A factorial is the product of an integer and all the integers below it;
e.g., factorial four ( 4! ) is equal to 24, because 4 * 3 * 2 * 1 equals 24. factorial zero 
(0!) is always 1.

    function factorial(x) {
        if (x == 0) return 1
        return x * factorial(x - 1)
    }
    console.log(factorial(7))
    console.log(factorial(5))
    console.log(factorial(2))

Problem 4: Recursion
example 12: collect Strings
Write a function called collectStrings which accepts an object and returns 
an array of all the values in the object that have a typeof string
collectStrings(obj) // ["foo", "bar", "baz"])
recursion with helper
    const obj = { name: "Bob", age: "80 years old", height: "3 feet", location: "Maine" }

    function collectStrings(obj) {

        let str = Object.entries(obj).map(([key, value]) => (
            typeof value === 'string' ? value : collectStrings(value)
        ))
        return str
    }
    console.log(collectStrings(obj));

Problem #5: Bubble Sort
Given the following data structure
    const data = [ 
    {
    name: 'John Smith', 
    age: new Map([['age', 88]]), 
    favoriteMovie: [ 
    {
    title: 'Hulk', 
    genre: 'action', 
    rating: 6
    }
    ] 
    },
    {
    name: 'Tony Kim', 
    age: new Map([['age', 3]]), 
    favoriteMovie: [ 
    {
    title: 'Top Gun', 
    genre: 'action', 
    rating: 10
    }
    ] 
    },
    {
    name: 'John Smith', 
    age: new Map([['age', 35]]), 
    favoriteMovie: [ 
    {
    title: 'Saw', 
    genre: 'horror', 
    rating: 8
    }
    ] 
    }
    ]
Using the bubble sort, please sort each profile
by ascending order for the following properties: 
*** If you want to know how to retrieve a value from a map, 
please see https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/getage (solution should look like)

    const sortedByAge = [ 
    {
    name: 'Tony Kim', 
    age: new Map([['age', 3]]), 
    favoriteMovie: [ 
    {
    title: 'Top Gun', 
    genre: 'action', 
    rating: 10
    }
    ] 
    },
    {
    name: 'John Smith', 
    age: new Map([['age', 35]]), 
    favoriteMovie: [ 
    {
    title: 'Saw', 
    genre: 'horror', 
    rating: 8
    }
    ] 
    },
    {
    name: 'John Smith', 
    age: new Map([['age', 88]]), 
    favoriteMovie: [ 
    {
    title: 'Hulk', 
    genre: 'action', 
    rating: 6
    }
    ] 
    }
    ]

    function ageSort(data) {
        let copyData = [...data]
        for (let i = 1; i < copyData.length; i++) {
            if (copyData[i].age.get('age') < copyData[i - 1].age.get('age')) {
                let temp = copyData[i];
                copyData[i] = copyData[i - 1];
                copyData[i - 1] = temp;
            }
        }

        return copyData
    }

    console.log(ageSort(data))
favorite movie by rating (solution should look like)

    const sortedByRating = [ 
    {
    name: 'John Smith', 
    age: new Map([['age', 88]]), 
    favoriteMovie: [ 
    {
    title: 'Hulk', 
    genre: 'action', 
    rating: 6
    }
    ] 
    },
    {
    name: 'John Smith', 
    age: new Map([['age', 35]]), 
    favoriteMovie: [ 
    {
    title: 'Saw', 
    genre: 'horror', 
    rating: 8
    }
    ] 
    },
    {
    name: 'Tony Kim', 
    age: new Map([['age', 3]]), 
    favoriteMovie: [ 
    {
    title: 'Top Gun', 
    genre: 'action', 
    rating: 10
    }
    ] 
    }
    ]