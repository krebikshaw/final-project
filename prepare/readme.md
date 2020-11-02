# Product Spec 第一階段版本
### 修訂紀錄

|日期|內容|人員|
|-|-|-|
|2020.11.01|新增統整系統架構 + 新增註冊、登入、編輯資料功能|裕翔|
|2020.11.02|新增聯絡平台、聯絡賣家功能|裕翔|




### ☞ 產品簡介與功能(Product Value)

#### 產品名稱：
* 待確認

#### 產品簡介：
* <產品名稱> 為一個二手物品交易平台，提供一個簡易及便利的交易環境

#### 產品目標說明：
* <產品名稱> 不是為了提供大型賣家成立電商網站，而是要讓一般的市民朋友，家裡有用不到的東西時，可以放上平台，彼此交換的物品的一個共享網站。不提供商業用途（促銷、優惠方案、團購優惠）等功能，只提供簡單的「找尋物品」&「刊登物品」兩項功能。本產品不具備商業目標，故本平台不會向賣方或買方酌收任何手續費用。

### ☞ 系統架構：

[會員系統](#會員系統)
* [註冊功能](#註冊功能)
* [登入功能](#登入功能)
* [資料編輯功能](#資料編輯功能)
* [權限確認功能](#權限確認功能)
* [聯絡平台功能](#聯絡平台功能)
* [聯絡賣家功能](#聯絡賣家功能)

[商品系統](#商品系統)
* [搜尋功能](#搜尋功能)
* [分類功能](#分類功能)
* [刊登功能](#刊登功能)
* [管理功能](#管理功能)

[訂單系統](#訂單系統)
* [編輯狀態功能](#編輯狀態功能)

[購物車系統](#購物車系統)
* [成立訂單功能](#成立訂單功能)
* [即時更新功能](#即時更新功能)

[後台管理系統](#後台管理系統)
* [用戶管理功能](#用戶管理功能)
* [商品管理功能](#商品管理功能)
* [編輯條款功能](#編輯條款功能)

[網站系統](#網站系統)
* [幫助功能](#幫助功能)
* [通知中心功能](#通知中心功能)
* [常見問題及條款功能](#常見問題及條款功能)

[資料庫欄位表](#資料庫欄位表)

## 權限分級

| 權限   | 分級 | 管理員 | 賣家 | 用戶 | 路人 |
| ------ | ---- | ------ | ---- | ---- | ---- |
| 所有人 | 1    | O      | O    | O    | O    |
| 用戶   | 2    | O      | O    | O    |      |
| 賣家   | 3    | O      | O    |      |      |
| 管理員 | 4    | O      |      |      |      |

## 會員系統

### 註冊功能
#### ☞ 描述
第一階段僅需讓使用者自行輸入帳號密碼即可，不需要串接 facebook 或 google 的登入方法

#### ☞ 條件
|角色|權限|狀態|
|-|-|-|
|路人|1|未登入|

#### ☞ 路由

##### 註冊/登入頁面

###### 路由
| 路由                      | 按鈕 |
| ------------------------- | ---- |
| 前往[註冊頁面](#註冊頁面) | 註冊 |


##### 註冊頁面

###### 操作
| 操作 | 按鈕 | Method | 後端 API      | NEXT             |
| --- | ---- | ------ | ------------- | ---------------- |
| 註冊網站 | 註冊 | POST   | demo/register | 註冊成功回到首頁 |


#### ☞ 介面
##### 註冊/登入頁面
![](https://i.imgur.com/1n8CGbN.png)
|元素|規則|
|- |- |
|註冊按鈕|跳至註冊頁面|
|登入按鈕|跳至登入頁面|
![](https://i.imgur.com/FeZvQEw.png)


##### 註冊頁面
![](https://i.imgur.com/1rk8fbE.png)
|元素|規則|錯誤提示|
|- |- |- |
|帳號|必填 + 僅接受英文、數字、符號 + 不接受空行|帳號格式錯誤|
|密碼|必填 + 僅接受英文、數字、符號 + 不接受空行|密碼格式錯誤|
|信箱|必填 + 需含有 @ 字元|信箱格式錯誤|
|註冊|跳至首頁||
![](https://i.imgur.com/t4S6aep.png)


#### ☞ 邏輯
![](https://i.imgur.com/rIwntXP.png)

|流程|規則|
|-|-|
|驗證|確認欄位是否符合規則、確認帳號是否已被註冊|

#### ☞ 異常情形處理
暫無

#### ☞ 資料結構

|欄位|型態|長度|必填|預設|備註|
|-|-|-|-|-|-|
|帳號|varchar|24|Y|||
|密碼|varchar|64|Y||需經過 hash|
|信箱|varchar|24|Y|||

### 登入功能
#### ☞ 描述
第一階段僅需讓使用者自行輸入帳號密碼即可，不需要串接 facebook 或 google 的登入方法

#### ☞ 條件
|角色|權限|狀態|
|-|-|-|
|路人|1|未登入|

#### ☞ 路由

##### 註冊/登入頁面

###### 路由
| 路由                      | 按鈕 |
| ------------------------- | ---- |
| 前往[註冊頁面](#註冊頁面) | 註冊 |
| 前往[登入頁面](#登入頁面) | 登入 |


##### 登入頁面

###### 操作
| 操作 | 按鈕 | Method | 後端 API   | NEXT             |
| --- | ---- | ------ | ---------- | ---------------- |
| 登入網站 | 登入 | POST   | demo/login | 登入成功回到首頁 |

#### ☞ 介面
##### 登入介面
![](https://i.imgur.com/UjF1yNr.png)
|元素|規則|錯誤提示|
|- |- |- |
|帳號|必填 + 僅接受英文、數字、符號 + 不接受空行|帳號或密碼錯誤|
|密碼|必填 + 僅接受英文、數字、符號 + 不接受空行|帳號或密碼錯誤|
|登入|跳至首頁||
![](https://i.imgur.com/nrwYSyi.png)


#### ☞ 邏輯
![](https://i.imgur.com/xt5IpoU.png)
|流程|規則|
|-|-|
|驗證|確認欄位是否符合規則、確認帳號密碼是否正確|


#### ☞ 異常情形處理
暫無

#### ☞ 資料結構

|欄位|型態|長度|必填|預設|備註|
|-|-|-|-|-|-|
|帳號|varchar|24|Y|||
|密碼|varchar|64|Y||需經過 hash|

### 資料編輯功能
#### ☞ 描述
包含編輯個人資料、編輯賣家資料、編輯賣家公告等功能

#### ☞ 條件
|類型|角色|權限|狀態|
|-|-|-|-|
|編輯個人資料|用戶|2|登入|
|編輯賣家資料|用戶|3|登入 + 賣家身份|
|編輯賣家公告|用戶|3|登入 + 賣家身份|

#### ☞ 路由
##### 我的資料頁面
###### 渲染
| 說明                 | Method | 後端 API      |
| -------------------- | ------ | ------------- |
| 取得自己的使用者資料 | GET    | demo/user/:id |

###### 路由
| 路由                              | 按鈕     |
| --------------------------------- | -------- |
| 前往[重設密碼頁面](#重設密碼頁面) | 重設密碼 |
| 回到上一頁                        | 返回     |


###### 操作
| 操作     | 按鈕     | Method | 後端 API      | 備註                           |
| -------- | -------- | ------ | ------------- | ------------------------------ |
| 更改照片 | 選擇照片 |        |               | 串 Imgur API 將 url 放進 input |
| 更改內容 | 更新     | PATCH  | demo/user/:id |                                |


##### 重設密碼頁面

###### 路由
| 路由       | 按鈕 |
| ---------- | ---- |
| 回到上一頁 | 返回 |

###### 操作
| 操作       | 按鈕 | Method | 後端 API      | 備註 |
| ---------- | ---- | ------ | ------------- | ---- |
| 更改密碼   | 更新 | PATCH  | demo/user/:id |      |
| 驗證 EMAIL | 驗證 | POST   |               |      |

##### 我的賣家資料頁面

###### 渲染
| 說明                   | Method | 後端 API        |
| ---------------------- | ------ | --------------- |
| 取得該使用者的賣家資料 | GET    | demo/vendor/:id |

###### 路由
| 路由       | 按鈕 |
| ---------- | ---- |
| 前往[重設密碼頁面](#重設密碼頁面) | 重設密碼 |
| 回到上一頁 | 返回 |

###### 操作
| 操作              | 按鈕     | Method | 後端 API        | 備註                           |
| ----------------- | -------- | ------ | --------------- | ------------------------------ |
| 上傳大頭貼        | 選擇圖片 |        |                 | 串 Imgur API 將 url 放進 input |
| 上傳 Banner       | 選擇圖片 |        |                 | 串 Imgur API 將 url 放進 input |
| 上傳 Line QR Code | 選擇圖片 |        |                 | 串 Imgur API 將 url 放進 input |
| 更改賣家資料      | 更新     | PATCH  | demo/vendor/:id |                                |

##### 編輯賣家公告視窗

###### 渲染
| 說明         | Method | 後端 API              |
| ------------ | ------ | --------------------- |
| 取得自己的賣家公告 | GET    | demo/vendor/:id |

###### 操作
| 操作               | 按鈕 | Method | 後端 API        | 備註 |
| ------------------ | ---- | ------ | --------------- | ---- |
| 修改自己的賣家公告 | 更新 | PATCH  | demo/vendor/:id |      |

#### ☞ 介面
##### 我的資料頁面
![](https://i.imgur.com/MiCDIMa.png)
|元素|規則|錯誤提示|
|- |- |- |
|姓名|必填 + 不接受空行|此欄位為必填|
|暱稱|必填 + 不接受空行|此欄位為必填|
|地址|必填 + 不接受空行|此欄位為必填|
|電子郵件|必填 + 不接受空行 + 需包含 @ 字元|此欄位為必填|
|生日|必填|此欄位為必填|
|大頭照|檔案大小 <= 1000K|照片檔案過大|
(mobile 頁面待補)

##### 重設密碼頁面
![](https://i.imgur.com/LyP1bg6.png)
|元素|規則|錯誤提示|
|- |- |- |
|舊密碼|必填 + 不接受空行|此欄位為必填|
|新密碼|必填 + 不接受空行|此欄位為必填|
|再次輸入新密碼|必填 + 不接受空行|此欄位為必填|
|電子郵件|必填 + 不接受空行 + 需包含 @ 字元|此欄位為必填|
![](https://i.imgur.com/Aedv2WD.png)

##### 我的賣家資料頁面
![](https://i.imgur.com/pgHTSqx.png)
|元素|規則|錯誤提示|
|- |- |- |
|姓名|必填 + 不接受空行|此欄位為必填|
|暱稱|必填 + 不接受空行|此欄位為必填|
|身分證字號|必填 + 不接受空行 + 第一碼為大寫英文 + 長度需為 10 碼|此欄位為必填|
|地址|必填 + 不接受空行|此欄位為必填|
|電子郵件|必填 + 不接受空行 + 需包含 @ 字元|此欄位為必填|
|生日|必填|此欄位為必填|
|QRcode|檔案大小 <= 500K|照片檔案過大|
|大頭照|檔案大小 <= 1000K|照片檔案過大|
|封面照|檔案大小 <= 1500K|照片檔案過大|
|匯款帳號|銀行代碼 + 帳號|帳號規格不符|
![](https://i.imgur.com/sUGm8AZ.png)

##### 編輯賣家公告視窗
![](https://i.imgur.com/Jni14x8.png)
|元素|規則|錯誤提示|
|- |- |- |
|輸入框|x|x|
(mobile 頁面待補)

#### ☞ 邏輯
![](https://i.imgur.com/fCNIsp0.png)
|流程|規則|
|-|-|
|非敏感資訊|確認欄位是否符合規則|
|敏感資訊|確認欄位是否符合規則 + 確認驗證是否通過|
|賣家公告|x|


#### ☞ 異常情形處理
暫無

#### ☞ 資料結構

|欄位|型態|長度|必填|預設|備註|
|-|-|-|-|-|-|
|姓名|varchar|24|Y|||
|暱稱|varchar|64|Y|||
|密碼|varchar|64|Y||需經過 hash|
|信箱|varchar|24|Y|||
|生日|datetime||Y|||
|地址|varchar|24|Y|||
|LINE ID|varchar|24||||
|頭貼 Url|varchar|24||||
|封面照 Url|varchar|24||||
|身分證字號|varchar|24|Y|||
|匯款帳號|varchar|24|Y|||

### 權限確認功能
#### ☞ 描述
一般用戶註冊後即享有購買權限
開通賣家身份後，方可擁有刊登權限

#### ☞ 條件
|類型|角色|權限|狀態|
|-|-|-|-|
|編輯資料|用戶|2 or 3|登入|
|刊登商品|用戶|3|登入 + 賣家身份|


#### ☞ 介面
##### 申請成為賣家頁面
![](https://i.imgur.com/p14R4gl.png)
|元素|規則|錯誤提示|
|- |- |- |
|身分證字號|必填 + 不接受空行 + 開頭為大寫英文 + 長度 = 10碼|欄位規格不符|
(mobile 頁面待補)

#### ☞ 邏輯
![](https://i.imgur.com/v8B7xvS.png)
|流程|規則|
|-|-|
|註冊|確認欄位是否符合規則|
|開通賣家資格|確認欄位是否符合規則 + 確認驗證是否通過|


#### ☞ 異常情形處理
暫無

#### ☞ 資料結構
|欄位|型態|長度|必填|預設|備註|
|-|-|-|-|-|-|
|身分證字號|varchar|24|Y|||

### 聯絡平台功能
#### ☞ 描述
兩種方式：
1. 透過表單方式，向平台提出意見
2. 透過「幫助按鈕」以聊天視窗方式，與平台進行溝通

#### ☞ 條件
|類型|角色|權限|狀態|
|-|-|-|-|
|表單方式|任何|1|x|
|聊天視窗|用戶|2|登入|

#### ☞ 路由
路由
| 路由       | 按鈕 |
| ---------- | ---- |
| 回到上一頁 | 取消 |

操作
| 操作         | 按鈕 | Method | 後端 API | 備註 |
| ------------ | ---- | ------ | -------- | ---- |
| 提交內容 | 送出 | POST   |          |      |

#### ☞ 介面
##### 表單頁面
![](https://i.imgur.com/ZSUInkl.png)
|元素|規則|錯誤提示|
|- |- |- |
|姓名|必填 + 不接受空行|此欄位為必填|
|電子郵件|必填 + 不接受空行 + 需包含 @ 字元|此欄位為必填|
|電話|必填 + 不接受空行|此欄位為必填|
|內容|必填|此欄位為必填|
![](https://i.imgur.com/2ilpNdi.png)

##### 聊天系統頁面
![](https://i.imgur.com/RoZkWby.png)
|元素|規則|錯誤提示|
|- |- |- |
|輸入留言|必填|此欄位為必填|

#### ☞ 邏輯
|流程|規則|
|-|-|
|送出|確認欄位是否符合規則|
(mobile 頁面待補)

#### ☞ 異常情形處理
暫無
#### ☞ 資料結構
|欄位|型態|長度|必填|預設|備註|
|-|-|-|-|-|-|
|身份|varchar|24|Y|||
|內容|text||Y|||

### 聯絡賣家功能
#### ☞ 描述
賣家可設定電子信箱、電話、Line QRcode
使用者可查看賣家聯絡資訊，主動聯絡賣家

#### ☞ 條件
|類型|角色|權限|狀態|
|-|-|-|-|
|查看賣家聯絡資訊|任何|1|x|

#### ☞ 路由
##### 聯絡賣家視窗
###### 渲染
| 說明                   | Method | 後端 API |
| ---------------------- | ------ | -------- |
| 取得該賣家資料 | GET    | demo/vendor/:id   |

#### ☞ 介面
![](https://i.imgur.com/2ByMGfA.png)
(mobile 頁面待補)

#### ☞ 邏輯
暫無

#### ☞ 異常情形處理
暫無

#### ☞ 資料結構
暫無

------

## 商品系統
### 搜尋功能
#### ☞ 描述
#### ☞ 條件
#### ☞ 路由
#### ☞ 介面
#### ☞ 邏輯
#### ☞ 異常情形處理
#### ☞ 資料結構

### 分類功能
#### ☞ 描述
#### ☞ 條件
#### ☞ 路由
#### ☞ 介面
#### ☞ 邏輯
#### ☞ 異常情形處理
#### ☞ 資料結構

### 刊登功能
#### ☞ 描述
#### ☞ 條件
#### ☞ 路由
#### ☞ 介面
#### ☞ 邏輯
#### ☞ 異常情形處理
#### ☞ 資料結構

### 管理功能
#### ☞ 描述
#### ☞ 條件
#### ☞ 路由
#### ☞ 介面
#### ☞ 邏輯
#### ☞ 異常情形處理
#### ☞ 資料結構

------

## 訂單系統
### 編輯狀態功能

------

## 購物車系統
### 成立訂單功能
### 即時更新功能

------

## 後台管理系統
### 用戶管理功能
### 商品管理功能
### 編輯條款功能

------

## 網站系統
### 幫助功能
### 通知中心功能
### 常見問題及條款功能

------



## 資料庫欄位表
```
Table users {
  id int PK 
  username varchar  
  password varchar 
  nickname varchar
  email varchar
  address varchar // 地址
  role tinyint  // 0:一般用戶、1:管理員
  is_vendor tinyint // 0: 非賣家、1:已開通賣家
  announcment text // 賣家頁面的公告
  account varchar // 賣家匯款帳號
  socialmedia_id varchar // 暫定為 LINE 帳號
  birthday datetime
  id_card_no varchar // 身份證字號
  avatar_url varchar // 使用者照片
  banner_url varchar // 賣家頁面的 banner 圖片
  status tinyint // 0: 正常、1：停權
  deletedAt timestamp
  createdAt datetime
  updatedAt datetime
}

Table boards {
  id int
  UserId int
  createdAt datetime
  updatedAt datetime
}

Table board_comments {
  id int
  user_id int
  comment varchar
  deletedAt timestamp
  createdAt datetime
  updatedAt datetime
}

Table products {
  id int PK
  name varchar
  CategoryId int
  picture_url varchar // 上傳 Imgur 後的圖片 URL
  info text // 商品敘述
  price int
  quantity int
  delivery tinyint // 出貨方式  0:面交、1:郵寄
  status tinyint // 0: 未審查、1:已審核通過、2:未通過
  UserId int // 關聯到 users，識別此商品的賣家
  deletedAt timestamp
  createdAt datetime
  updatedAt datetime
}

Table product_categories {
  id int PK
  name varchar
  deletedAt timestamp
  createdAt datetime
  updatedAt datetime
}

Table orders {
  id int PK
  order_number int // unique 訂單編號，例如 AE20201101001
  seller_id int // 關聯到 users，識別此訂單賣家
  client_id int // 關聯到 users，識別此訂單買家
  total_quantity init // 訂單總數量
  shipping init // 訂單運費
  total_amount int // 訂單總金額
  content varchar // 訂單備註內容
  client_address varchar 
  client_email varchar
  is_paid tinyint
  // *是否付款：0 未付款、1 已付款、2 已收到退款
  is_sent tinyint
  // *是否寄送：0 賣家未出貨、1 賣家點選已出貨
  is_completed tinyint
  // *是否完成交易：0 訂單未完成、1 訂單已完成、2 訂單取消中、3 訂單已取消
  is_refunded tinyint
  // *是否完成交易：0 未退款、1 已退款
  createdAt datetime
  updatedAt datetime
}

Table order_items {
  id int PK
  ProductId int // 關聯 product，拿到此項 order item 的商品細節
  OrderId int // 關聯 order，識別此 order item 是屬於哪張訂單
  product_name varchar // 下單商品名稱
  product_quantity int // 下單商品數量
  product_price int // 下單商品價格，若此價格跟實際商品價格有出入，則通知買家後刷新價格
  createdAt datetime 
  updatedAt datetime
}

Table carts {
  id int PK
  seller_id int // 關聯到 users，識別此購物車的賣家
  client_id int // 關聯到 users，識別此購物車的買家
  createdAt datetime
  updatedAt datetime
}

Table cart_items {
  id int PK
  ProductId int
  CartId int // 關連到 carts，識別是哪一輛購物車
  is_empty tinyint // 0: 正常狀態、1:沒庫存購物車失效凍結
  product_name varchar
  product_quantity int
  product_price int
  createdAt datetime
  updatedAt datetime
}

Table faq {
  id int PK
  question text
  Faqs_categoryId int
  answer text
  deletedAt timestamp
  createdAt datetime
  updatedAt datetime
}

Table faq_categories {
  id int PK
  name varchar
  deletedAt timestamp
  createdAt datetime
  updatedAt datetime
}

Table rules {
  id int PK
  rule text
  content text
  deletedAt timestamp
  createdAt datetime
  updatedAt datetime
}

Ref: "products"."CategoryId" < "product_categories"."id"
Ref: "products"."UserId" < "users"."id"
Ref: "orders"."seller_id" < "users"."id"
Ref: "orders"."client_id" < "users"."id"
Ref: "order_items"."OrderId" < "orders"."id"
Ref: "order_items"."ProductId" < "products"."id"
Ref: "cart_items"."ProductId" < "products"."id"
Ref: "cart_items"."CartId" < "carts"."id"
Ref: "carts"."seller_id" < "users"."id"
Ref: "carts"."client_id" < "users"."id"
Ref: "boards"."UserId" < "users"."id"
Ref: "faq"."Faqs_categoryId" < "faq_categories"."id"

Ref: "board_comments"."user_id" < "boards"."UserId"
```


