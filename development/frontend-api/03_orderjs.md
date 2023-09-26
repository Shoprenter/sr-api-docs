# Order.js

On the successful order page, you can place scripts that can access the data of the given order. 

The **lastOrder** property of the ShopRenter javascript object contains the data related to the order, such as the general data (delivery and payment method, currency, etc.) and the data of the ordered products.

The object does not contain sensitive data on the basis of which the Buyer could be identified.

Example:
```javascript
console.log(ShopRenter.lastOrder);
```

### Meaning of some fields:

<table> 
    <tr>
        <th>property</th>
        <th>meaning</th>
    </tr>
    <tr>
        <td>id</td>
        <td>order id</td>
    </tr>
    <tr>
        <td>customerGroup</td>
        <td>customer group</td>
    </tr>  
    <tr>
        <td>total</td>
        <td>Total amount payable after ordering</td>
    </tr> 
    <tr>
        <td>orderStatusId</td>
        <td>Identifier of the post-order status</td>
    </tr>
    <tr>
        <td>currency</td>
        <td>The currency in which the order was placed</td>
    </tr>
    <tr>
        <td>dateAdded</td>
        <td>The date the order was created</td>
    </tr>
    <tr>
        <td>shipping.methodName</td>
        <td>The delivery method is the name displayed in the language of the order</td>
    </tr>
    <tr>
        <td>shipping.methodCode</td>
        <td>Text identifier of the shipping method</td>
    </tr>
    <tr>
        <td>shipping.country</td>
        <td>Country name, in the language of the order</td>
    </tr>
    <tr>
        <td>shipping.countryId</td>
        <td>The country identifier</td>
    </tr>
    <tr>
        <td>shipping.vatRate</td>
        <td>VAT amount for the delivery method</td>
    </tr>
    <tr>
        <td>shipping.expectedDelivery</td>
        <td>Expected delivery time in timestamp</td>
    </tr>
    <tr>
        <td>payment.methodName</td>
        <td>The name of the payment method displayed in the language of the order</td>
    </tr>
    <tr>
        <td>payment.methodCode</td>
        <td>The text identifier of the payment method</td>
    </tr>
    <tr>
        <td>payment.vatRate</td>
        <td>VAT rate for the payment method</td>
    </tr>
    <tr>
        <td>coupon.id</td>
        <td>Identifier of the coupon</td>
    </tr>
    <tr>
        <td>coupon.vatRate</td>
        <td>The rate of VAT for the coupon.</td>
    </tr>
    <tr>
        <td>products</td>
        <td>Includes the products in the order</td>
    </tr>
    <tr>
        <td>products.id</td>
        <td>Identifier of the product</td>
    </tr>
    <tr>
        <td>products.title</td>
        <td>Product name</td>
    </tr>
    <tr>
        <td>products.unitPrice</td>
        <td>Unit price of the product</td>
    </tr>
    <tr>
        <td>products.totalPrice</td>
        <td>Total price of the product (quantity * unit price)</td>
    </tr>
    <tr>
        <td>products.vatRate</td>
        <td>The rate of VAT for the product</td>
    </tr>
    <tr>
        <td>products.quantity</td>
        <td>Quantity</td>
    </tr>
    <tr>
        <td>products.sku</td>
        <td>Article number of the product</td>
    </tr>
    <tr>
        <td>products.giftWrapping</td>
        <td>Data on the gift packaging requested by the Customer for each product. If you do not request packaging for the given product, there will be an empty array on this property</td>
    </tr>
    <tr>
        <td>products.giftWrapping.id</td>
        <td>The internal identifier of the package</td>
    </tr>
    <tr>
        <td>products.giftWrapping.sku</td>
        <td>Article number of the packaging</td>
    </tr>
    <tr>
        <td>products.giftWrapping.price</td>
        <td>Net price of packaging</td>
    </tr>
    <tr>
        <td>products.giftWrapping.vat</td>
        <td>VAT of packaging</td>
    </tr>
    <tr>
        <td>products.giftWrapping.name</td>
        <td>Name of the package</td>
    </tr>
    <tr>
        <td>products.giftWrapping.quantityName</td>
        <td>The name of the packaging unit, e.g. box</td>
    </tr>
    <tr>
        <td>giftWrapping</td>
        <td>The basket's gift wrapping. Although its structure is the same as when we pack the products individually. If the Buyer does not request packaging for the entire basket, there will be an empty block on this property</td>
    </tr>
    <tr>
        <td>loyaltyPoints</td>
        <td>Data of the loyalty point used in the order. If the loyalty point system is not enabled, or no loyalty points were used for the given order, there is an empty array on this property</td>
    </tr>
    <tr>
        <td>loyaltyPoints.usedPoints</td>
        <td>The number of points used in the order</td>
    </tr>
    <tr>
        <td>loyaltyPoints.valueOfOnePoint</td>
        <td>Value of one point in HUF</td>
    </tr>
    <tr>
        <td>loyaltyPoints.vatRate</td>
        <td>VAT value. It only affects the transfer to the invoicing program, it does not change the value of the loyalty point.</td>
    </tr>
    <tr>
        <td>loyaltyPoints.totalValue</td>
        <td>The total amount covered by the Customer with loyalty points during the order. This is displayed converted to the currency corresponding to the order. (<strong>currency</strong> property)</td>
    </tr>
</table>
