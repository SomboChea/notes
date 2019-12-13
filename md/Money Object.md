
# Coding Guides

-  How to use Money Value Object?
	-
	First way, you can create an object instance from Money:
	```java
	// create a new money instance
	MoneyObject money = MoneyObject.create(1000, MoneyCurrency.KHR)
									.addMoney(10, MoneyCurrency.USD)
									.addMoney(10, MoneyCurrency.EUR)
									.compute();
	``` 
	Second way, you create with Money Rules Statement:
	```java
	String moneyRules = "1000:KHR,10:USD";
	MoneyObject money = MoneyObject.parse(moneyRules);
	```
	And more you do like this:
	```java
	// create a new money instance
	MoneyObject money = MoneyObject.create(1000, MoneyCurrency.KHR)
									.addMoney(10, MoneyCurrency.USD)
									.compute();
	// create a new money instance
	MoneyObject addMore100Money = MoneyObject.create(100, MoneyCurrency.USD);
	// add money instance to exists money
	money.addMoney(addMore100Money);
	// compute money again
	money.compute();
	```
	**Note*** Money Currency will be use First Money create. But if you allow money.auto-currency to false. It will be use default money from app config.
<br />
<br />
<br />
<br />
### Response Demo
```json
// 20191212195935
// http://url/money?rules=3000:KHR,10:usd,200000:khr,5:USD,2.55:USD

{
  "value": 273200.0,
  "currency": "KHR",
  "currency_format": "៛",
  "display_value": "273,200",
  "display_format": "៛ 273,200",
  "auto_currency": true,
  "default_currency": "USD",
  "ceil_on_value": false,
  "floor_on_value": false,
  "computed": true,
  "money_states": [
    {
      "value": "3000.0",
      "currency": "KHR",
      "history": {
        "valueOn": "Thu Dec 12 19:59:34 ICT 2019",
        "valueOf": "4000.0",
        "currency": "KHR"
      }
    },
    {
      "value": "10.0",
      "currency": "USD",
      "history": {
        "valueOn": "Thu Dec 12 19:59:34 ICT 2019",
        "valueOf": "1.0",
        "currency": "USD"
      }
    },
    {
      "value": "200000.0",
      "currency": "KHR",
      "history": {
        "valueOn": "Thu Dec 12 19:59:34 ICT 2019",
        "valueOf": "4000.0",
        "currency": "KHR"
      }
    },
    {
      "value": "5.0",
      "currency": "USD",
      "history": {
        "valueOn": "Thu Dec 12 19:59:34 ICT 2019",
        "valueOf": "1.0",
        "currency": "USD"
      }
    },
    {
      "value": "2.55",
      "currency": "USD",
      "history": {
        "valueOn": "Thu Dec 12 19:59:34 ICT 2019",
        "valueOf": "1.0",
        "currency": "USD"
      }
    }
  ]
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYyNzQ5OTc3OV19
-->