# BlockChain Assignment - 1

##### Test Type: Create New Order - 1 (User 1)

Function Call - addOrder(100)

Description: As user 1 place a new order

Desired Outcome: Transaction doesn't fail and when an orderid is added to the list when clicking getorderids on remix

Actual Outcome: Order Added. getorderids shows added transaction with id 1.

Result: Pass





##### Test Type: Create New Order - 2 (User 1)

Function Call - addOrder(10)

Description: As user 1 place a new order

Desired Outcome: Transaction doesn't fail and when an orderid is added to the list when clicking getorderids on remix

Actual Outcome: Order Added. getorderids shows added transaction with id 2.

Result: Pass







##### Test Type: Accept Order (User 1)

Function Call - acceptOrder(1)

Description: As user 1 try to accept order with id 1

Desired Outcome: Transaction Fails

Actual Outcome: Transaction fails and error is thrown on console.

Result: Pass






##### Test Type: Accept Order (User 2)

Function Call - acceptOrder(1)

Description: As user 2 try to accept order with id 1

Desired Outcome: Transaction Fails since payment has not been done.

Actual Outcome: Transaction fails and error is thrown on console.

Result: Pass




##### Test Type: Pay For Order (User 2)

Function Call - payForOrder(1)

Description: As user 2 try to pay for order with id 1

Desired Outcome: Transaction Fails since payment has to be done by user 1 who created the order.

Actual Outcome: Transaction fails and error is thrown on console.

Result: Pass







##### Test Type: Get order ids

Function Call - getOrderIds()

Description: Get All the order ids that are in transit (either order added, payment made but order not accepted)

Desired Outcome: Returns list of order ids in transit

Actual Outcome: [1,2] (Payment not made for any order)

Result: Pass




##### Test Type: Pay For Order (User 1)

Function Call - payForOrder(1)

Description: As user 1 try to pay for order with id 1

Desired Outcome: Transaction passes and status of paid updated to true. Can also see payment transaction in logs.

Actual Outcome: Transaction fails and error is thrown on console.

```json
[
	{
		"from": "0x1482717eb2ea8ecd81d2d8c403cacf87acf04927",
		"topic": "0x737c69225d647e5994eab1a6c301bf6d9232beb2759ae1e27a8966b4732bc489",
		"event": "Paid",
		"args": {
			"0": "0x5B38Da6a701c568545dCfcB03FcB875f56beddC4",
			"1": "25000",
			"length": 2
		}
	}
]
```

Result: Pass




##### Test Type: Get order ids

Function Call - getOrderIds()

Description: Get All the order ids that are in transit (either order added, payment made but order not accepted)

Desired Outcome: Returns list of order ids in transit

Actual Outcome: [1,2] (Payment has been made for order id 1 but it has not been accepted)

Result: Pass




##### Test Type: Accept Order (User 2)

Function Call - acceptOrder(1)

Description: As user 2 try to accept order with id 1 for which payment is done

Desired Outcome: Transaction passes. Logs created that show the address of user who accepted, 

Actual Outcome: Transaction passes

```json
[
	{
		"from": "0x1482717eb2ea8ecd81d2d8c403cacf87acf04927",
		"topic": "0xb5559c1275a840104410004719c28e16c16237edd69f34d27dcdb2616fd79894",
		"event": "Accepted",
		"args": {
			"0": "0xAb8483F64d9C6d1EcF9b849Ae677dD3315835cb2",
			"1": "3",
			"2": "25000",
			"length": 3
		}
	}
]
```

Result: Pass




##### Test Type: Get order ids

Function Call - getOrderIds

Description: Get All the order ids that are in transit (either order added, payment made but order not accepted)

Desired Outcome: Returns list of order ids in transit

Actual Outcome: [2] (Order id 1 was accepted in last test case and so only order id 2 is returned)

Result: Pass
