# Spin-Wheel-for-Discount
<b>Simple HTML and JavaScript spin the wheel for discount.</b>

Here's an explanation of how to use the `rewards` array and the `weight` property:

The `rewards` array is a collection of objects that represent the possible outcomes of the spin wheel. Each object in the array has three properties:

1. `label`: This is the text that will be displayed as the reward on the spin wheel.
2. `message`: This is the message that will be shown when the corresponding reward is selected.
3. `weight`: This is a numerical value that determines the probability of the corresponding reward being selected.

The `weight` property is used to assign a relative probability to each reward. The higher the `weight` value, the more likely the reward will be selected. Here's how it works:

1. The `weights` array is created by mapping the `rewards` array and extracting the `weight` values of each reward object.
2. The `totalWeight` variable is the sum of all the `weight` values in the `weights` array.
3. When the `spinWheel` function is called, a random number is generated between 0 and `totalWeight`.
4. The `rewards` array is then iterated over, and a cumulative sum of the `weight` values is calculated.
5. The reward whose cumulative weight exceeds the randomly generated number is selected as the winner.

For example, in the provided `rewards` array, the `weight` values are:

- '40% discount': 10
- '30% discount': 20
- '20% discount': 20
- '10% discount': 20
- '0% discount': 20
- '50% discount': 10

The `totalWeight` is the sum of these weights, which is 100.

When the `spinWheel` function is called, a random number between 0 and 100 is generated (let's say it's 50).

The cumulative sum of weights is calculated as follows:

- '40% discount': 10 (less than 50, so not selected)
- '30% discount': 10 + 20 = 30 (less than 50, so not selected)
- '20% discount': 30 + 20 = 50 (equal to the random number, so this reward is selected)

So, in this example, the '20% discount' reward will be selected.

By adjusting the `weight` values, you can control the probability of each reward being selected. For example, if you want the '50% discount' reward to be more likely, you can increase its `weight` value relative to the others.

It's important to note that the sum of all `weight` values should be greater than 0 for the probability calculation to work correctly.

Here is an example how to make the '50% discount', '40% discount', and '30% discount' rewards less likely to be landed on, we can decrease their `weight` values relative to the other rewards. Here's an example:

```javascript
const rewards = [
    { label: '40% discount', message: 'This is the message that appears for <b>40% discount</b>', weight: 5 },
    { label: '30% discount', message: 'This is the message that appears for <b>30% discount</b>', weight: 10 },
    { label: '20% discount', message: 'This is the message that appears for <b>20% discount</b>', weight: 25 },
    { label: '10% discount', message: 'This is the message that appears for <b>10% discount</b>', weight: 25 },
    { label: '0% discount', message: 'This is the message that appears for <b>0% discount</b>', weight: 30 },
    { label: '50% discount', message: 'This is the message that appears for <b>50% discount</b>', weight: 5 },
];
```

In this example, we've decreased the `weight` values of '50% discount', '40% discount', and '30% discount' to 5, 5, and 10, respectively. At the same time, we've increased the `weight` values of '20% discount', '10% discount', and '0% discount' to 25, 25, and 30, respectively.

The `totalWeight` in this case is 100 (5 + 10 + 25 + 25 + 30 + 5).

With these changes, the probability of landing on each reward is as follows:

- '50% discount': 5/100 = 5% probability
- '40% discount': 5/100 = 5% probability
- '30% discount': 10/100 = 10% probability
- '20% discount': 25/100 = 25% probability
- '10% discount': 25/100 = 25% probability
- '0% discount': 30/100 = 30% probability

So, the '50% discount', '40% discount', and '30% discount' rewards are now less likely to be selected compared to the other rewards.

You can further adjust the `weight` values to fine-tune the probabilities as per your requirements. Just remember that the sum of all `weight` values should be greater than 0, and the higher the `weight` value, the more likely the reward will be selected.

=> NOTE: there is a version without localstorage and allows unlimited spins: discount-wheel.html with js/wheel_no_storage.js

<b>Brought to you by https://discountplr.com</b>
