# Payment plan for recurring payments

It is essential to have payment plans for Recurring payments.
We can edit our payment plans on https://billing.shoprenter.hu/plans.
After logging in, you can see a list of our existing plans and add new ones.

Changing the price and name of the payment plan also affects existing subscriptions,
if one of the two data is changed, the next fee payment period for existing subscriptions is based on the new data.

Payment plans list page:

![Image 1](../image/plan1.jpg)


Create a new payment plan:

![Image 2](../image/plan2.jpg)

| Input                             | Description                                                                                    |
|-----------------------------------|------------------------------------------------------------------------------------------------|
| Payment plan name | Here you can enter the name of the plan. Eg: "Bronze package of my application" |
| Length of payment cycles | Here you can specify at what intervals the amount requested for using the application should be deducted |
| Number of payment cycles | Here you can enter the number of times the shop owner's card will be debited |
| Net price of payment plan in HUF | The net price. For VAT calculation, see: [Invoicing and VAT calculation](../docs/price_calc.md) |

On the list page, we can refer to each Payment plan with the value in the **Identifier** column,
when we want to create a Recurring fee payment through the API.

[Example for recurring charge payment](../docs/recurring_charge.md)
