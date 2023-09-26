# Extend Resource

Extended resources make data exchange easier. We have two such resources currently, **productExtend** and **orderExtend**.
The point of these resources is that their related data is also returned in the response.
So, e.g. in case of a product, no further request is necessary to receive its description, discount, customer group price,  etc.

Furthermore, these details can be modified within a resource with a single request.
However, request types have completely different operations here.

In the case of a **POST** request, we always create the related data (*Related Resource in Resource documentation).
Illustrated with an example: A product is in 2 categories. If we send 3 categories with a POST request, then these will be assigned in addition, therefore the product will be included in 5 categories. If the relation of a category already exists, then we will not perform the POST request, receiving the error message that the connection of the current category already exists.

In the case of a **PUT** request, the related data (*Related Resource in Resource documentation) is overwritten.
Illustrated with a similar example: A product is in 2 categories. If we send 3 categories with a PUT request, then the already existing categories will be overwritten by the sent 3. So after the successful request, the product will only be listed in those 3 categories that were included in the request. In this case we will not receive any error message, even if we sent already existing categories. The existing categories are simply replaced by the sent ones.
Furthermore, we can exclude the product from categories with a PUT request. Then we send an empty block instead of categories. This way we replace the existing categories with empty ones, so there will be no categories.

In the API technical documentation, the word **Extend** after the resource names indicates which resources have this functionality.
So, the essence of resources is to be able to query their related data as well directly in the response. Therefore in case of a product, no further request is necessary to receive its description, discount, customer group price,  etc.

These details can also be modified within a resource with a single request, however request types have completely different functions, depending on the relationship between the related and the current resource.

## OneToMany relation

E.g. more descriptions may belong to a product. Product Descriptions in the case of Product Extend.

In the case of a **POST** request, we always create the related data (*Related Resource in Resource documentation).

Illustrated with an example: A product is in 2 categories. If we send 3 categories with a POST request, then these will be assigned in addition, therefore the product will be included in 5 categories. If the relation of a category already exists, then we will not perform the POST request, receiving the error message that the connection of the current category already exists.

In the case of a **PUT** request, the related data (*Related Resource in Resource documentation) is overwritten.
Illustrated with a similar example: A product is in 2 categories. If we send 3 categories with a PUT request, then the already existing categories will be overwritten by the sent 3. So after the successful request, the product will only be listed in those 3 categories that were included in the request. In this case we will not receive any error message, even if we sent already existing categories. The existing categories are simply replaced by the sent ones.
Furthermore, we can exclude the product from categories with a PUT request. Then we send an empty block instead of categories. This way we replace the existing categories with empty ones, so there will be no categories.

## OneToOne relation

E.g. A product may belong to only one producer. Manufacturer in the case of Product Extend. (This is the only available OneToOne relation at the moment.)

The operation of POST and PUT is the same in the case of an Extend resource field of such.

1. If the sent data block that belongs to a OneToOne field includes only one resource id, then if a related resource exists, the previous one will be replaced.
   E.g. If we send a POST request in which there is only one resource id related to the **manufacturer** data, to a Product Extend resource, then the system will try to replace the previous manufacturer with the newly sent one.

2. If the sent data block that belongs to a OneToOne field includes only fields and corresponding values, but no resource id, then we create a new related resource and link this one to the original Extend resource.
   E.g. If send a POST request that includes only data related to the **manufacturer** but no resource id, to an Extend resource, then the system creates the new manufacturer and connects it to the product.

3. If the sent data block that belongs to a OneToOne field includes resource id, fields and corresponding values as well, then the system will try to update the already existing resource related to the resource id, otherwise the resource will be created.

## ManyToMany relation

E.g. Several countries may belong to a geographical zone, and a country may belong to several geographical zones.

Currently, only GeoZone and Country resources have such a relationship. It can only accept GET individual and collection requests.
1. Starting from the **GeoZone** resource, in the case of a **GET** request, we have to provide the resource id of a geographic zone, e.g. the geographical zone of the European Union. In the response, in addition to the simple properties, we can find which countries belong to it in the **countries** property. In this case, for example: Hungary, Austria... etc.

2. Starting from the **Country** resource, in the case of a **GET** request, we have to provide the resource id of a country, e.g. Hungary. In the response, in addition to the simple properties, we will receive which geographical zones include the country, in the **geoZones** property. In this case, for the geographic zones of Hungary and the European Union.
