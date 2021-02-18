# Mcpetrade API Wrapper
API Wrapper для взаимодействия с mcpetrade.com
## Подключение

``` js
const {
    MCPETrade
} = require('mcpetrade-api')
const mc = new MCPETrade({"shop": shopId, "server": serverId})
```

## Методы API
***createPayment*** - создать счет на оплату
| Параметр | Тип | Обязателен | Описание |
|--|--|--|--|
| productId | number | Да | ID продукта |
| username | string | Да | Ник пользователя |
| coupon | string | Нет | Скидочный купон |
**Пример**
``` js
async function createPayment() {
let payment = mc.createPayment(104252, 'test') 
console.log(payment) // { status: 'success', response: 'https://pay.mcpetrade.com?account=1234' }
}
createPayment().catch(console.error)
```
