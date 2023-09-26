# Delete application

If the application is deleted, the system automatically cancels the currently running Recurring payments in the given store.
Then, ShopRenter sends a **GET** HTTP request to the uninstallUrl specified during application registration, thereby indicating the fact of deletion.

The GET request contains 4 query parameters:
- shopName: the name of the shop in which the application was deleted
- code: Generated hash
- timestamp: Request time
- hmac: Check hash

The code, timestamp and hmac parameters are used to verify the request. More info on hmac checking is [here](https://github.com/Shoprenter/developers/blob/master/app-development/GETTING_STARTED.md).
