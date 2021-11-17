# task-4

Provide a solution to the following problem:
Premise: An SQL table has 4 columns: product, region, province, price. The region column can be either National or Provincial. If region is Provincial then province is filled (e.g. Ontario), otherwise it's blank. Each product has one national price, but may have zero or one provincial price. If a product has no provincial price, the national price is used. For example, "kale" may have a provincial price of $5.99 in Ontario and a national price of $4.50, with no other prices. If a user wanted to find the price of kale in Quebec they would get $4.50.
Challenge: Create a method, with a name and signature, that finds the price of a particular product in a particular province. Add the logic in pseudo-code to the body of the method. Be sure to include input parameters, a return statement, and any validation or exception handling that you deem necessary. You can represent the data as an array of objects.


Solution:
Let us assume a REST type environment with data from SQL being received in the form of JSON.
This would imply, the following:

For data of product *kale* in region *Quebec* we recieve the following Data:


```json
{
	"Product": "kale",
	"Province": "National",
	"Price": "$4.50",
}

```

We write a function as follows:

_Assuming the function getData will get us json type data_

```go
type productDetails struct {
  Product string `json:"product"`
  Region  string `json:"region"`
  Province string `json:"province"`
  Price string `json:"price"`
}
func checkPrice(provinceName string, productName string) (int, error) {
  var data []productDetails = getData() //Returns JSON type data [Already marshalled into our data struct]
  for (each product) in data {
    if data.Province == nil {
      err:= new Errorf("National Prices available only")
      return int(data.Price), err
     } else {
      return int(data.Price), _
    }
  }
}

```
