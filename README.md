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

***getServers*** - получить все сервера привязанные к вашему магазину

**Пример**
``` js
async function getServers() {
let servers = mc.getServers() 
console.log(servers) // { status: 'success', response: [ { id: '124', name: 'Test' } ] }
}
getServers().catch(console.error)
```

***getServers*** - получить онлайн серверов привязанных к магазину

**Пример**
``` js
async function getOnline() {
let online = mc.getOnline() 
console.log(online) // { status: 'success', response: [{id: '123',name: 'Test',domain: '',port: '19132',online: true,numplayers: 130,maxplayers: 10000}]}
}
getOnline().catch(console.error)
```

***getProducts*** - получить список продуктов магазина
| Параметр | Тип | Обязателен | Описание |
|--|--|--|--|
| category | string | Нет | Категория продукта |

**Пример**
``` js
async function getProducts() {
let products = mc.getProducts() 
console.log(products)
}
getProducts().catch(console.error)
```

***getPaymentStatus*** - получить состояние счета (оплачен или нет)
| Параметр | Тип | Обязателен | Описание |
|--|--|--|--|
| billId | number | Да | ID счета |

**Пример**
``` js
async function getPaymentStatus() {
let payment = mc.getPaymentStatus(123) 
console.log(payment) // { status: 'success', response: { status: 'waiting' } }
}
getPaymentStatus().catch(console.error)
```
