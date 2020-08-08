#badouyao 巴豆夭訂便當系統

- 基本資料表

- 職員資料
SELECT * FROM employees

- 職稱
SELECT * FROM employeePositions

- 餐廳
SELECT * FROM restaurants

- 食物
SELECT * FROM foods

- 訂單
SELECT * FROM orders

- 訂單明細
SELECT * FROM restaurants

- 列出職稱
SELECT lastName, firstName, p.positionName
FROM `employees` e JOIN employeePositions p
ON p.positionID = e.positionID

- 列出小醬臭豆腐【埔里總店】餐廳restaurantID = 3的食物
SELECT * 
FROM foods
WHERE restaurantID = 3

- 列出訂單
SELECT orderID, e.LastName, e.firstName, r.restaurantName 
FROM `orders` o 
JOIN employees e ON e.employeeID = o.employeeID
JOIN restaurants r ON r.restaurantID = o.restaurantID

- 列出有食物名稱的訂單明細
SELECT orderID, f.foodName, o.price, quantity, o.price*quantity AS totalPrice, optional 
FROM orderdetails o
JOIN foods f ON f.foodID = o.foodID


- 一併列出訂單明細
SELECT orderID, foodID, SUM(price*quantity) 
FROM orderdetails
GROUP BY orderID, foodID
WITH ROLLUP
