NOTE: AwsSum is now deprecated. Please use [aws-sdk](https://www.npmjs.org/package/aws-sdk) instead.

# awssum-amazon-elb #

This is an ```AwsSum``` plugin!

## Example

```javascript
var amazonElb = require('./awssum-amazon-elb.js');

var elb = new amazonElb.Elb({
	'accessKeyId'     : process.env.AWS_ACCESS_KEY_ID,
	'secretAccessKey' : process.env.AWS_SECRET_ACCESS_KEY,
	'region'          : 'us-east-1',
});

elb.DescribeLoadBalancers(function(err, data) {
	if (err) throw new Error(err);

	var balancers = data.Body.DescribeLoadBalancersResponse.DescribeLoadBalancersResult.LoadBalancerDescriptions.member;
	balancers.forEach(function(balancer) {
		console.log('%s : %s', balancer.CreatedTime, balancer.LoadBalancerName);
	});
});
```

(Ends)
