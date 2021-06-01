# PaymentCardInput deprecation
[PaymentCardInput](../operations.md#paymentcardinput) field of [configuration](../operations.md#configuration) object is deprecated and will be removed from the response of [configuration/get](../operations.md#getconfigurationinfo). It is replaced by [PaymentCardRequirement](../operations.md#paymentcardrequirement).

## Response diff

```diff
{
    ...
    "Configurations": [
        {
            ...
-           "PaymentCardInput": "NotRequested",
+           "PaymentCardRequirement": "NotRequired",
        }
    ]
}
```
