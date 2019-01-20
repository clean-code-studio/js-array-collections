###JS Collections Package

**Purpose:** Extends Javascript Array For Simpler Sorting & Filtering
**Motiviation:** Laravel Collections
**Other Package Content:** String Prototype Methods

By extending prototypes we are able to fluently chain methods together

#
**Examples:**
```
let posts = [
   {name: 'Good Morning Utah', id: 1, length: 9453, readers: 20000, status: 'published'},
   {name: 'Super Bowl Sunday', id: 2, length: 945, readers: 100, status: 'published'},
   {name: 'Machine Learning', id: 3, length: 119453, readers: 420000, status: 'internationally_published'},
   {name: 'Friday Night Lights', id: 4, length: 3343, readers: 1334, status: 'pending'}, 
];


posts.where('readers', '<=', 4500).pluck('status')
//returns ['published', 'pending']

posts.take(3).pluck('name').reverse().listify()
// returns 'Machine Learning, Super Bowl Sunday, Good Morning Utah'

posts.take(3).pluck('name').reverse().listify().truncate(35)
// returns 'Machine Learning, Super Bowl Sunday...'

```


#
**Array/Collection Methods:**

```

/**
 *
 * @param options
 * @returns {Array}
 */
 where(property, condition, value)
 where([[property, condition, value], [property, condition, value]]) 
 
 
/**
 *
 * @param property
 * @param context
 * @returns {*}
 */
orderBy(property, context = 'asc')


/**
 *
 * @returns {*[]}
 */
flatten()


/**
 *
 * @param property
 * @returns {*}
 */
flatPluck(property)


/**
 *
 * @param property
 * @returns {Array}
 */
groupBy(property)


/**
 *
 * @returns {string}
 */
stringify()


/**
 *
 * @returns {string}
 */
listify()


/**
 *
 * @returns {*}
 */
random()


/**
 *
 * @param $property
 * @param $condition
 * @param $expectation
 * @returns {*}
 */
where(property, condition, expectation)


/**
 *
 * @param callback
 * @returns {Array|Object}
 */
each(callback)


/**
 *
 * @returns {Array}
 */
tail()


/**
 *
 * @param number
 * @returns {*[]}
 */
take(numberOfElements)


/**
 *
 * @returns {*}
 */
first()


/**
 *
 * @returns {*}
 */
last()


/**
 *
 * @param options
 * @returns {Array}
 */
pluck(prop)


/**
 *
 * @returns {Array}
 */
unique()


/**
 *
 * @param args
 * @returns {Array}
 */
append(elements)


/**
 *
 * @param number
 * @returns {*}
 */
count()


/**
 *
 * @param by
 * @returns {Array}
 */
chunk(byIncrement)


/**
 *
 * @param $property
 * @param $condition
 * @param $expected
 * @returns {*}
 */
firstWhere(property, condition, expectation)


/**
 *
 * @param $property
 * @param $condition
 * @param $expected
 * @returns {*}
 */
lastWhere(property, condition, expectation)


/**
 *
 * @returns {*|number}
 */
sum()


/**
 *
 * @param array
 * @returns {*}
 */
intersect(array)


/**
 *
 * @returns {boolean}
 */
empty()


/**
 *
 * @returns {number}
 */
lastIndex()


/**
 *
 * @param args
 * @returns {Array}
 */
prepend(array)

```



#
**More Examples:**

```


//Example one - where
`let smallPosts = posts.where('readers', '<=', 100);`


`[{name: 'asdfasdfsdf', id: 2, length: 945, readers: 100, status:'published'}]`



//Example two - pluck property
`let names = post.pluck('name');`

`['Sunday Morning Post', 'asdfasdfsdf', 'dasdf', 'Friday Night Lights'];`


//Example three - chaining several find total reader from published posts

`let totalReadersFromActivePosts = posts.where('status', '=', 'published').pluck('readers').sum()`

`numberOfReadersAddedUpFromAllPublishedPosts`



//Example four - find the average number of readers where posts are not published

`let avgReadersForNonPublishedPosts = posts.where('status', '!=', 'published').pluck('readers').avg()`

`avg Number of readers for Non Published Posts`

```