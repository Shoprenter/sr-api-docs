# Initial steps

Since we use an API to create payment plans, the developer must always provide an interface within his application,
where the store owner can start the payment process. If e.g. we take the Recurring fee payment as a basis, our application may contain it
a sub-site where we can offer different monthly fee packages. After selecting the package, it sends a POST request accordingly
the application to the Payment API to create a Recurring Fee payment.

So what you will need:

- Subpage responsible for starting a purchase where all available payment options can be viewed. The functions belonging to the given packages must also be listed here!

- notificationUrl: It will send the API webhook to this Url about the events that happened during the payment. The management of these events must also be implemented.

- failedUrl and successUrl: The store owner will be directed to these pages, where they can receive information about the outcome of the payment.
