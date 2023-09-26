# Statuses

## Payments

Statuses belong to the two payment types, which provide information about the status of the life cycle of the given payment.
Although the two types have different life paths after the first successful transaction, the states that can be recorded by payments are largely the same

|Status                    | Description                                                                                                                                                                                                                                                                |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|pending                    | The status of the newly created pending payment.                                                                                                                                                                                                                           |
|accepted                   | The state before payment, when the store owner has accepted the payment conditions on the 'approve page'.                                                                                                                                                                  |
|active                     | Status after successful payment.                                                                                                                                                                                                                                           |
|declined | Declined payment. This can happen on the page confirming the payment or on the interface of the service that handles the transaction.                                                                                                                                      |
|expired | Recurring payments that have permanently expired can be assigned to this status. (No further charges need to be deducted.)                                                                                                                                                 |
|frozen | It can occur in the case of recurring payments, if an error occurs during the transaction due to problematic bank details of the store owner.                                                                                                                              |
|failed | An error occurred in the bank card payment service that cannot be resolved or continued.                                                                                                                                                                                   |
|cancelled | If the Recurring payment is in FROZEN status, after 15 days - if it has not been possible to restore it to ACTIVE status - it will be in this status. In addition, if the payment is directly interrupted, e.g. when deleting an application, the status will be CANCELED. |

## Bank card change

They provide information on the status of the life cycle of a bank card exchange carried out for a specific Recurring fee payment.
Similar situations can be observed as in the case of normal payments, since technically every exchange corresponds to a bank card payment.

|Status                    | Description                                                                                                                                                    |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|pending | The status of the newly created, pending ban card replacement. |
|accepted | The state before payment, when the store owner has accepted the exchange as the confirmer. |
|active | Status after a successful exchange transaction. The fee of HUF 10 has been deducted and the Recurring fee payment will be made from the new card at the next charge |
|declined | Rejected exchange. This can happen on the page confirming the payment or on the interface of the service that handles the transaction. |
|failed | Or an error occurred in the bank card payment service or in the Payment API that cannot be resolved or continued. |

