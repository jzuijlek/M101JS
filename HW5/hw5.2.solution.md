# Homework Assignment 5.2 Solution

This homework is a multiple choice question; you can find the answer to the question by running the following command in the hands-on shell in the homework page itself.

```javascript
db.zips.aggregate([
	{
		$match : { 
			"state" : {$in : ["CA", "NY"] } 
		}
	},
	{
		$group : {
			_id : { state: '$state', city: '$city'}, 
			sum_pop : { $sum: '$pop' }
		}
	},
	{ 
		$match : { 
			"sum_pop" : {$gt : 25000}
		} 
	},
	{
		$group : {
			_id : null,
			'average': {$avg: "$sum_pop"}
		}
	},
]);
```
