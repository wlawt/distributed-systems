# Vending Machine Problem
You need to write code to implement a Vending machine that has a bunch of products like chocolates, candy, cold-drink, and accept some coins like Nickle, Dime, Quarter, Cent, etc. Make sure you insert a coin, get a product back, and get your chance back. Also, write the Unit test to demonstrate that these common use cases work.

- Time provided (30-45 mins)

### Requirements
- Support n list of products
- Accept variety of coins (i.e. Nickle, Dime, Quarter, Cent)
    - Return back a product from there

### API Design
At its basic, we can have 2 functions:

`process_payment(Array product, Double, coins)`

`get_product(Array product)`

### Database Design
- For this problem I don't think we need one. At most you can have a cache where you keep track of the `current_payment(Array product, Double coins)` to deal with refunding if something fails or to ensure a product has been returned (cross-validating).

### Logic to Solve
1. Have a state to keep track of the product(s) (would be a queue) 
2. Have a counter increasing for n amount of coins inserted with the appropriate value
3. `process_payment` by:
    - Updating the counter with the amount and then popping off the product from the queue
    - Calculate the amount to charge
4. `get_product` by: 
    - Calculating the difference and accepting the payment
    - Returning the product (send it out the machine) 
    - Return the difference (if any) 
5. Clear the cache

### System Workflow
![System Workflow](https://github.com/wlawt/distributed-systems/blob/master/img/VendingMachine.jpg)

### Caching
- Overall, this is simple, but it will keep track of the `current_payment` and reset when the transaction is complete (i.e. returns True). To ensure a product has been sent or coins have been returned, we can compare the boolean of the `get_product` returns and if `current_payment` is reset with default values. If not, we can issue back the coins inserted. 

### Messaging Queue
- A standard queue will suffice for single request applications

### Points that weren't considered
- Load balancer
- Hashing (consistent hashing) 
- LRU
- Hadoop
- Cassandra
- Microservices

This is because the large majority of this system handles a single request at a time so scalability and load isn't a huge concern. 
