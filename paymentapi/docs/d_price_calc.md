# Billing data and VAT calculation

ShopRenter automatically retrieves the invoicing data from the owner's store. Therefore, it does not require any further action
by the application developer.

However, what you absolutely need to know is how the invoicing data affects the calculation of the current VAT.

### Who issues the invoice?

In all cases, the invoice is issued in the name of ShopRenter.

### In what cases can the gross sum differ from the current Hungarian VAT content?

It is determined by two factors: the **country** registered for the store and the existence of the **community tax number**.

**Accordingly, 4 cases are possible:**
1. The store is operated by a Hungarian company and does not have a community tax number: **27% VAT**

2. The store operator belongs to an EU member state, but does not have a community tax number: **27% VAT**

3. The store operator belongs to an EU member state and has a community tax number: **0%**

4. The store operator is from 3rd country: **0%**

### Incomplete billing information

It may happen that in the specific store where I want to install the application in question,
has incomplete billing data.
So when creating [One Time](../docs/g_one_time_charge.md) and [Recurring Charge](../docs/i_recurring_charge.md), we can get an error message that the system sees missing billing data. This is error code 40019.

In this case, the application must draw the attention of the store operator to replace the missing billing data in the "My Account" menu item of the admin interface.

**The message will contain a logId, which must be sent to the email address partnersupport@shoprenter.hu.
ShopRenters colleagues will take care of filling in the missing data.**
