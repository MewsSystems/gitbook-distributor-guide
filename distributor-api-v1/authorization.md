# Authorization

The Distributor API is a public API with no authorization, it suffices to know unique identifier of a hotel in order to access it. However it is required that the client would identify itself by providing the `Client` property in all requests made to the API. As an example, have a look at [Get Hotel Info](operations.md#get-hotel-info) operation.

It is also a good practice to include version info, which makes potential problem investigation much simpler. For example our client uses the following identification `MEWS Distributor [version]`.

