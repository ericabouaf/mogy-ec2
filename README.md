# mogy-ec2

Amazon EC2 activities for [mogy](https://github.com/neyric/mogy).

## Installation

In your mogy project, install the dependency using npm :

$ npm install mogy-ec2 --save

To register the ec2 activities to Amazon Simple Workflow :

$ mogy register

## Config

In your mogy environment config file, under the `activities` key, add :

````json
"ec2": {
    "region": "us-east-1"
}
````

:warning: This activity is not able to use a different user than the AWS mogy user yet.
Be sure to give that IAM user EC2 privileges.

## Sample Decider Usage

````javascript
activity({
    name: 'my-task',
    activity: 'ec2_runInstances',
    input: {
        ImageId: 'ami-2058e248',
        MinCount: 1,
        MaxCount: 1,
        UserData: "This is some cool user data\nOuyeah\n",
        InstanceType: "t1.micro",
        KeyName: "my-key",
        SecurityGroups: ["my-security-group"]
    }
})
````

For a detailed documentation, cf <http://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/EC2.html>
