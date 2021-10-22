# Purchase flow

On `init` of `SubscriptionViewModel`, Observers and Fetching of products are called
```
startObservers()
fetchProducts()
```

Inside the `StoreManager` there are 3 publisher that the `SubscriptionViewModel` subscribes

```
var productsSubject = PassthroughSubject<[SKProduct], Never>()
var validationResponse = PassthroughSubject<ReceiptValidationResult, Never>()
var restoreResponse = PassthroughSubject<PurchaseRestoreResponse, Never>()
```

When a user purchases a product, `SubscriptionViewModel` will trigger the 
```
func purchaseProduct(product: SKProduct)
```
in `StoreManager` and will receive a callback in 
```
func paymentQueue(_ queue: SKPaymentQueue, updatedTransactions transactions: [SKPaymentTransaction])
```
delegate
