# Liquid-in-a-Soda-Machine
0

You are given an array of integers representing a range of requested soda in ml (milliliters). The soda machine has three buttons on it. Pressing the first button will dispense between 200ml and 205ml of soda. Pressing the second button dispenses between 300ml and 305ml. Pressing the third button dispenses between 400ml and 405ml.

Create an AWS Lambda application written using Flask (Python) with 2 functions that are exposed via HTTP endpoints:

FIrst endpoint (Manual):

Accepts a POST request at /api/manual with the following JSON body:
{
"buttonNumber": 1, // can be 2 or 3
"targetVolume": 500 // can be any valid non-negative integer. This is passed in with each request and cannot be changed until isBelowTarget is false. The system resets after isBelowTarget becomes false.
}
The response will be JSON as per the sample below:
{
"quantityRequested": 300,
"isBelowTarget": true // false if target has been exceeded
} 
Multiple manual requests are required to test if the target has been reached.
Second endpoint (Auto):

Accepts a GET request at /api/auto with only the targetVolume:
{
"targetVolume": 500
}
The response will be JSON as per the sample below:
{
"button1": 1,
"button2: 1
}
The response indicates how many button presses of each type is required to reach the target. Any empty object is returned if no combination of button presses is possible.
Expectations:

You may use any framework (Serverless, SAM etc.) to create the service.
Authentication is not required.
You must cater for error handling.
You must deploy the service and share the URL to access it. Use AWS's free tier for this purpose.
You must share your code via a remote repo (Github/Bitbucket for example). This can be a public repo to make it easier to access.
 
Examples for auto mode:
 

solve(605)
> true
The target is 605 milliliters. This could be achieved by pressing the first button three times, or by pressing the second button twice

Example #2
solve(100)
> false
The target is 100 milliliters. There aren't any combination of buttons we could press to dispense 100ml, so return false

 

Once you are done, please also complete the following:

Create 4 additional endpoints:

1.         Login - accepts a username and password and checks the DB if the user exists and creates a session using cookies so that subsequent authenticated requests are accepted for the next 1 hour.

2.         Sign up - Creates a new user by accepting a username and password.

3.         Sign out - Invalidates an active session

4.         View history - A list of user's submitted inputs and the result including the date and time when each was submitted.
