**---
title: New Huo Brokerage API 文檔

language_tabs: # must be one of https://git.io/vQNgJ
- json

toc_footers:
- <a href='https://www.trade.newhuotech.com/zh-hk/trade/api'>創建 API Key </a>
  includes:

search: true
---

# 更新日誌

<style>
table {
    max-width:100%
}
table th {
    white-space: nowrap; /*表頭內容強製在一行顯示*/
}
</style>



| 生效時間<br>(UTC +8) | 接口     | 變化      | 摘要         |
| ---------- | --------- | --------- | --------------- |
| 2022.01.17 | - | - | - |


# 簡介
---
title: New Huo Brokerage API 文檔

language_tabs: # must be one of https://git.io/vQNgJ
- json

toc_footers:
- <a href='https://www.trade.newhuotech.com/zh-hk/trade/api'>創建 API Key </a>
  includes:

search: true
---

# 更新日誌

<style>
table {
    max-width:100%
}
table th {
    white-space: nowrap; /*表頭內容強製在一行顯示*/
}
</style>



| 生效時間<br>(UTC +8) | 接口     | 變化      | 摘要         |
| ---------- | --------- | --------- | --------------- |
| 2022.01.17 | - | - | - |


# 簡介

歡迎使用New Huo Brokerage API！

此文檔是New Huo Brokerage API的唯一官方文檔，New Huo Brokerage API提供的功能和服務會在此文檔持續更新。

以下是Brokerage OTC API文檔各章節主要內容

第一部分是概要介紹：

- **快速入門**：該章節對New Huo Brokerage API做了簡單且全方位的介紹，適合第一次使用New Huo Brokerage API的用戶。
- **常見問題**：該章節列舉了使用New Huo Brokerage API時常見的、和具體API無關的通用問題。
- **聯系我們**：該章節介紹了針對不同問題，如何聯系我們。

第二部分是每個接口類的詳細介紹，每個接口類一個章節，每個章節分為如下內容：

- **簡介**：對該接口類進行簡單介紹，包括一些註意事項和說明。
- ***具體接口***：介紹每個接口的用途、限頻、請求、參數、返回等詳細信息。
- **常見錯誤碼**：介紹該接口類下常見的錯誤碼及其說明。
- **常見問題**：介紹該接口類下常見問題和解答。

# 快速入門

## 接入準備

如需使用API ，請先登錄網頁端，完成API key的申請和權限配置，再據此文檔詳情進行開發和交易。

您可以點擊 <a href='https://www.trade.newhuotech.com/zh-hk/trade/api' >這裏 </a> 創建 API Key。

每個用戶可創建20組Api Key，每個Api Key可對應設置讀取權限。

權限說明如下：

- 讀取權限：讀取權限用於對數據的查詢接口，例如：資產列表查詢等。

創建成功後請務必記住以下信息：

- `Access Key`  API 訪問密鑰

- `Secret Key`  簽名認證加密所使用的密鑰（僅申請時可見）

<aside class="notice">
每個 API Key 最多可綁定 20個IP 地址(主機地址或網絡地址)。
</aside>
<aside class="warning">
<red><b>風險提示</b></red>：這兩個密鑰與賬號安全緊密相關，無論何時都請勿將二者<b>同時</b>向其它人透露。API Key的泄露可能會造成您的資產損失（即使未開通提幣權限），若發現API Key泄露請盡快刪除該API Key。
</aside>

## SDK與代碼示例

[Java](https://github.com/newhuo-tech/newhuo_Java) | [Python3](https://github.com/newhuo-tech/newhuo_Python) | [C++](https://github.com/newhuo-tech/newhuo_Cpp) | [C#](https://github.com/newhuo-tech/newhuo_CSharp) | [Go](https://github.com/newhuo-tech/newhuo_golang)

**其它代碼示例**

[https://github.com/newhuo-tech?tab=repositories](https://github.com/newhuo-tech?tab=repositories)

## 接口類型

Brokerage OTC 目前為用戶提供RESTFUL接口，您可根據自己的使用場景進行對接。

### REST API

REST，即Representational State Transfer的縮寫，是目前較為流行的基於HTTP的一種通信機製，每一個URL代表一種資源。

建議開發者使用REST API進行操作。

**接口鑒權**

目前只提供私有接口，私有接口可用於交易管理和賬戶管理。每個私有請求必須使用您的API Key進行簽名驗證。

## 接入URLs
您可以使用api.trade.newhuotech.com域名。

**REST API**

**`https://api.trade.newhuotech.com`**

<aside class="notice">
請使用中國大陸以外的 IP 訪問New Huo Brokerage API。
</aside>
<aside class="notice">
鑒於延遲高和穩定性差等原因，不建議通過代理的方式訪問New Huo Brokerage API。
</aside>
<aside class="notice">
為保證API服務的穩定性，建議使用日本AWS雲服務器進行訪問。如使用中國大陸境內的客戶端服務器，連接的穩定性將難以保證。
</aside>

## 簽名認證

### 簽名說明

API 請求在通過 internet 傳輸的過程中極有可能被篡改，為了確保請求未被更改，除公共接口（基礎信息，行情數據）外的私有接口均必須使用您的 API Key 做簽名認證，以校驗參數或參數值在傳輸途中是否發生了更改。
每一個API Key需要有適當的權限才能訪問相應的接口，每個新創建的API Key都需要分配權限。在使用接口前，請查看每個接口的權限類型，並確認你的API Key有相應的權限。
805
一個合法的請求由以下幾部分組成：

- 方法請求地址：即訪問服務器地址 api.trade.newhuotech.com，比如 api.trade.newhuotech.com/v1/open/apiKeyDemo。
- API 訪問Id（AccessKeyId）：您申請的 API Key 中的 Access Key。
- 簽名方法（SignatureMethod）：用戶計算簽名的基於哈希的協議，此處使用 HmacSHA256。
- 簽名版本（SignatureVersion）：簽名協議的版本，此處使用2。
- 時間戳（Timestamp）：您發出請求的時間 (UTC 時間)  。如：2017-05-11T16:22:06。在查詢請求中包含此值有助於防止第三方截取您的請求。
- 必選和可選參數：每個方法都有一組用於定義 API 調用的必需參數和可選參數。可以在每個方法的說明中查看這些參數及其含義。
  - 對於 GET 請求，每個方法自帶的參數都需要進行簽名運算。
  - 對於 POST 請求，每個方法自帶的參數不進行簽名認證，並且需要放在 body 中。
- 簽名：簽名計算得出的值，用於確保簽名有效和未被篡改。

### 簽名步驟

規範要計算簽名的請求 因為使用 HMAC 進行簽名計算時，使用不同內容計算得到的結果會完全不同。所以在進行簽名計算前，請先對請求進行規範化處理。下面以查詢某訂單詳情請求為例進行說明：

查詢某訂單詳情時完整的請求URL

`https://api.trade.newhuotech.com/v1/open/apiKeyDemo?`

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`&SignatureMethod=HmacSHA256`

`&SignatureVersion=2`

`&Timestamp=2017-05-11T15:19:30`

`&order-id=1234567890`

**1. 請求方法（GET 或 POST），後面添加換行符 「\n」**

例如：
`GET\n`

**2. 添加小寫的訪問域名，後面添加換行符 「\n」**

例如：
`
api.trade.newhuotech.com\n
`

**3. 訪問方法的路徑，後面添加換行符 「\n」**

例如apiKeyDemo：<br>
`
/v1/open/apiKeyDemo\n
`

例如WebSocket v2<br>
`
/ws/v2
`

**4. 對參數進行URL編碼，並且按照ASCII碼順序進行排序**

例如，下面是請求參數的原始順序，且進行URL編碼後


`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`demo-id=1234567890`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

<aside class="notice">
使用 UTF-8 編碼，且進行了 URL 編碼，十六進製字符必須大寫，如 「:」 會被編碼為 「%3A」 ，空格被編碼為 「%20」。
</aside>
<aside class="notice">
時間戳（Timestamp）需要以YYYY-MM-DDThh:mm:ss格式添加並且進行 URL 編碼。時間戳有效時間5分鐘。
</aside>

經過排序之後

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

`demo-id=1234567890`

**5. 按照以上順序，將各參數使用字符 「&」 連接**


`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2017-05-11T15%3A19%3A30&demo-id=1234567890`

**6. 組成最終的要進行簽名計算的字符串如下**

`GET\n`

`api.trade.newhuotech.com\n`

`v1/open/apiKeyDemo\n`

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2017-05-11T15%3A19%3A30&demo-id=1234567890`


**7. 用上一步裏生成的 「請求字符串」 和你的密鑰 (Secret Key) 生成一個數字簽名**


1. 將上一步得到的請求字符串和 API 私鑰作為兩個參數，調用HmacSHA256哈希函數來獲得哈希值。
2. 將此哈希值用base-64編碼，得到的值作為此次接口調用的數字簽名。

`4F65x5A2bLyMWVQj3Aqp+B4w+ivaA7n5Oi2SuYtCJ9o=`

**8. 將生成的數字簽名加入到請求裏**

對於Rest接口：

1. 把所有必須的認證參數添加到接口調用的路徑參數裏
2. 把數字簽名在URL編碼後加入到路徑參數裏，參數名為「Signature」。

最終，發送到服務器的 API 請求應該為

`https://api.trade.newhuotech.com/v1/open/apiKeyDemo?AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx&demo-id=1234567890&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2017-05-11T15%3A19%3A30&Signature=4F65x5A2bLyMWVQj3Aqp%2BB4w%2BivaA7n5Oi2SuYtCJ9o%3D`


# 接入說明

## 接口概覽

| 接口分類       | 分類鏈接                     | 概述                                             |
| -------------- | ---------------------------- | ------------------------------------------------ |


該分類為大類整理，部分接口未遵循此規則，請根據需求查看有關接口文檔。

## 新限頻規則

- 當前，新限頻規則正在逐步上線中，已單獨標註限頻值的接口且該限頻值被標註為NEW的接口適用新限頻規則。

- 新限頻規則采用基於UID的限頻機製，即，同一UID下各API Key同時對某單個節點請求的頻率不能超出單位時間內該節點最大允許訪問次數的限製。

- 用戶可根據Http Header中的"X-HB-RateLimit-Requests-Remain"（限頻剩余次數）及"X-HB-RateLimit-Requests-Expire"（窗口過期時間）查看當前限頻使用情況，以及所在時間窗口的過期時間，根據該數值動態調整您的請求頻率。

## 限頻規則

除已單獨標註限頻值為NEW的接口外 -<br>
* 每個API Key 在1秒之內限製10次<br>
* 若接口不需要API Key，則每個IP在1秒內限製10次<br>

比如：

* 資產訂單類接口調用根據API Key進行限頻：1秒10次


## 請求格式

所有的API請求都是restful，目前只有兩種方法：GET和POST

* GET請求：所有的參數都在路徑參數裏
* POST請求，所有參數以JSON格式發送在請求主體（body）裏

## 返回格式

所有的接口都是JSON格式。其中v1和v2接口的JSON定義略有區別。

**接口返回格式**：最上層有三個字段：`code`, `message` 和 `data`。前兩個字段表示返回碼和錯誤消息，實際的業務數據在`data`字段裏。

以下是一個返回格式的樣例：

```json
{
  "code": 200,
  "message": "",
  "data": // per API response data in nested JSON object
}
```

| 參數名稱 | 數據類型 | 描述               |
| -------- | -------- | ------------------ |
| code     | int      | API接口返回碼      |
| message  | string   | 錯誤消息（如果有） |
| data     | object   | 接口返回數據主體   |

## 數據類型

本文檔對JSON格式中數據類型的描述做如下約定：

- `string`: 字符串類型，用雙引號（"）引用
- `int`: 32位整數，主要涉及到狀態碼、大小、次數等
- `long`: 64位整數，主要涉及到Id和時間戳
- `float`: 浮點數，主要涉及到金額和價格，建議程序中使用高精度浮點型
- `object`: 對象，包含一個子對象{}
- `array`: 數組，包含多個對象

## 最佳實踐

###安全類
- 強烈建議：不要將API Key暴露給任何人（包括第三方軟件或機構），API Key代表了您的賬戶權限，API Key的暴露可能會對您的信息、資金造成損失，若API Key泄露，請盡快刪除並重新創建。

###公共類
**API訪問建議**

- 不建議在中國大陸境內使用臨時域名以及代理的方式訪問New Huo Brokerage API，此類方式訪問API連接的穩定性很難保證。
- 建議使用日本AWS雲服務器進行訪問。
- 官方域名api.trade.newhuotech.com。


**新限頻規則**

- 當前最新限頻規則正在逐步上線中，已單獨標註限頻值的接口適用新限頻規則。

- 用戶可根據Http Header中「X-HB-RateLimit-Requests-Remain（限頻剩余次數）」，「X-HB-RateLimit-Requests-Expire（窗口過期時間）」查看當前限頻使用情況，以及所在時間窗口的過期時間，根據該數值動態調整您的請求頻率。

- 同一UID下各API Key同時對某單個節點請求的頻率不能超出單位時間內該節點最大允許訪問次數的限製。


# 常見問題

本章列舉了和具體API無關的通用常見問題，如網絡、簽名或通用錯誤等。

針對某類或某個API的問題，請查看每章API的錯誤碼和常見問題。

### Q1：一個用戶可以申請多少個API Key？

每個用戶可創建20組API Key，每個API Key可對應設置讀取權限。

以下是權限的說明：

- 讀取權限：讀取權限用於對數據的查詢接口，例如：資產查詢等。

### Q2：為什麼經常出現斷線、超時的情況？

請檢查是否屬於以下情況：

1. 客戶端服務器如在中國大陸境內，連接的穩定性很難保證，建議使用日本AWS雲服務器進行訪問。

### Q3：為什麼簽名認證總返回失敗？

請檢查如下可能的原因：


1、簽名參數應該按照ASCII碼排序。比如下面是原始的參數：

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`order-id=1234567890`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

排序之後應該為：

`AccessKeyId=e2xxxxxx-99xxxxxx-84xxxxxx-7xxxx`

`SignatureMethod=HmacSHA256`

`SignatureVersion=2`

`Timestamp=2017-05-11T15%3A19%3A30`

`order-id=1234567890`

2、簽名串需進行URL編碼。比如：

- 冒號 `:`會被編碼為`%3A`，空格會被編碼為 `%20`
- 時間戳需要格式化為 `YYYY-MM-DDThh:mm:ss` ，經過URL編碼之後為 `2017-05-11T15%3A19%3A30`

3、簽名需進行 base64 編碼

4、Get請求參數需在簽名串中

5、時間為UTC時間轉換為YYYY-MM-DDTHH:mm:ss

6、檢查本機時間與標準時間是否存在偏差（偏差應小於1分鐘）

7、簽名時所帶Host應與請求接口時Host相同

如果您使用了代理，代理可能會改變請求Host，可以嘗試去掉代理；

或者，您使用的網絡連接庫可能會把端口包含在Host內，可以嘗試在簽名用到的Host中包含端口，如「api.trade.newhuotech.com:443"

8、Access Key 與 Secret Key中是否存在隱藏特殊字符，影響簽名

當前官方已支持多種語言的[SDK](https://github.com/newhuo-tech)，可以參考SDK的簽名實現，或者以下三種語言的簽名樣例代碼

<a href='https://github.com/newhuo-tech/newhuo_Java/blob/master/java_signature_demo.md'>JAVA簽名樣例代碼</a> | <a href='https://github.com/newhuo-tech/newhuo_Python/blob/master/example/python_signature_demo.md'>Python簽名樣例代碼</a>   | <a href='https://github.com/newhuo-tech/newhuo_Cpp/blob/master/examples/cpp_signature_demo.md'>C++簽名樣例代碼 </a>

### Q4：調用接口返回Incorrect Access Key 錯誤是什麼原因？

請檢查URL請求中Access Key是否傳遞準確，例如：

1. Access Key沒有傳遞
2. Access Key位數不準確
3. Access Key已經被刪除
4. URL請求中參數拼接錯誤或者特殊字符沒有進行編碼導致服務端對AccessKey解析不正確

### Q5：調用接口返回 gateway-internal-error 錯誤是什麼原因？

請檢查是否屬於以下情況：

1. 可能為網絡原因或服務內部錯誤，請稍後進行重試。
2. 發送數據格式是否正確（需要標準JSON格式）。
3. POST請求頭header需要聲明為`Content-Type:application/json` 。

### Q6：調用接口返回 login-required 錯誤是什麼原因？

請檢查是否屬於以下情況：

1. 未將AccessKey參數帶入URL中。
2. 未將Signature參數帶入URL中。

### Q7: 調用Rest接口返回HTTP 405錯誤 method-not-allowed 是什麼原因？

該錯誤表明調用了不存在的Rest接口，請檢查Rest接口路徑是否準確。由於Nginx的設置，請求路徑(Path)是大小寫敏感的，請嚴格按照文檔聲明的大小寫。

# 聯系我們

## 技術支持

使用過程中如有問題或者建議，您可選擇以下任一方式聯系我們：

- 通過官網的「幫助中心」或者發送郵件至cs@newhuotech.com聯系客服。

如您遇到API錯誤，請按照如下模板向我們反饋問題。

`1. 問題描述`
`2. 問題發生的用戶Id(UID)，賬戶Id和訂單Id(如果和賬戶、訂單有關系)`
`3. 完整的URL請求`
`4. 完整的JSON格式的請求參數（如果有）`
`5. 完整的JSON格式的返回結果`
`6. 問題出現時間和頻率（如何時開始出現，是否可以重現）`
`7. 簽名前字符串（如果是簽名認證錯誤）`


下方是一個應用了模版的例子：

`1. 問題簡要說明：簽名錯誤`
`2. UID：123456`
`3. 完整的URL請求：GET https://api.trade.newhuotech.com/v1/open/apiKeyDemo/forRead?&SignatureVersion=2&SignatureMethod=HmacSHA256&Timestamp=2019-11-06T03%3A25%3A39&AccessKeyId=rfhxxxxx-950000847-boooooo3-432c0&Signature=HhJwApXKpaLPewiYLczwfLkoTPnFPHgyF61iq0iTFF8%3D`
`4. 完整的JSON格式的參數：無`
`5. 完整的JSON格式的返回：{"status":"error","err-code":"api-signature-not-valid","err-msg":"Signature not valid: Incorrect Access key [Access key錯誤]","data":null}`
`6. 問題出現頻率：每次都會出現`
`7. 簽名前字符串`
`GET\n`
`api.trade.newhuotech.com\n`
`/v1/open/apiKeyDemo/forRead\n`
`AccessKeyId=rfhxxxxx-950000847-boooooo3-432c0&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=2019-11-06T03%3A26%3A13`

註意：Access Key僅能證明您的身份，不會影響您賬戶的安全。切記**不**要將Secret Key信息分享給任何人，若您不小心將Secret Key暴露，請盡快[刪除](https://www.hbg.com/zh-cn/apikey/)其對應的API Key，以免造成您的賬戶損失。

# 用戶相關

## 是否為授信用戶
用戶可以通過該接口查詢自己是否為授信用戶

### HTTP 請求

- GET `/open/otc/api/user/isCreditUser`

API Key 權限：讀取<br>

限頻值：10次/1s<br>

### 請求參數

> Response:

```json
{"code":200,"message":"success","data":true,"success":true,"messageArgs":[]}
```
### 響應數據

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">业务狀態码</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">錯誤信息（英文）</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">返回数据-泛型，支持各种返回的数据格式類型</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

## 是否為白名單用戶
用戶可以通過該接口查詢自己是否為白名單用戶

### HTTP 請求

- GET `/open/otc/api/user/isWhiteUser`

API Key 權限：讀取<br>

限頻值：10次/1s<br>

### 請求參數

> Response:

```json
{"code":200,"message":"success","data":false,"success":true,"messageArgs":[]}
```
### 響應數據
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">业务狀態码</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">錯誤信息（英文）</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">返回数据-泛型，支持各种返回的数据格式類型</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>


# 授信用戶相關

## 获取用戶待結算交易記錄
用戶可以通過該接口查詢自己待結算的交易記錄

### HTTP 請求

- POST `/open/otc/api/clearing/query`

API Key 權限：讀取<br>

限頻值：10次/1s<br>

### 請求參數
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> page</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">分頁查詢參數</span></td>
     <td key="5"></td>
    </tr>
          <tr key="0-0-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">每頁大小</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-0-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">當前頁數</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> side</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">買賣方向 1-買BUY 2-賣-SELL</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">基礎幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">計價幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> timeInForce</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">GTC,IOC,FOK；詢價交易只有FOK</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-5">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> startTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單時間-開始時間</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-6">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> endTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單時間-結束時間</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-7">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> orderId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-8">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> clearingStatus</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">清算狀態(0, "待清算"|1, "成交自動清算"|2, "部分清算"|3, "已完成"|4, "清算失敗")</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-9">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> tradeStatusList</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易狀態集合</span></td>
     <td key="5"><p key="3"><span style="font-weight: '700'"> </span><span></span></p></td>
    </tr>
    <tr key="0-10">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> clearingStatusList</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">清算狀態集合(0, "待清算"|1, "成交自動清算"|2, "部分清算"|3, "已完成"|4, "清算失敗")</span></td>
     <td key="5"><p key="3"><span style="font-weight: '700'"> </span><span></span></p></td>
    </tr>
     <tr key="0-11">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> ascending</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">正序(&quot;asc&quot;)還是倒序(&quot;desc&quot;)，默認是倒序</span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

> Response:

```json
{
    "code":200,
    "message":"success",
    "data":{
        "items":[
            {
                "id":2087,
                "orderId":1458097497309248,
                "side":1,
                "timeInForce":4,
                "baseCurrency":"ETH",
                "quoteCurrency":"HUSD",
                "quantity":"0.100000",
                "cumQuantity":"0.100000",
                "avgPx":"3238.948367",
                "lastPx":"3238.948367",
                "lastQty":"0.100000",
                "lastTurnover":"323.894837",
                "commission":"0 ETH",
                "transactionTime":1641959867582,
                "userId":11433212,
                "status":2,
                "symbolDisplayName":"ETHHUSD",
                "clearingStatus":0,
                "clearingAt":0,
                "clearingSourceId":"",
                "clearedQty":"0.000000",
                "clearedTurnover":"0.000000",
                "unClearedQty":"0.100000",
                "unClearedTurnover":"323.894837",
                "quantityPrecision":6,
                "amountPrecision":6
            },
            {
                "id":2089,
                "orderId":1458097518280768,
                "side":1,
                "timeInForce":4,
                "baseCurrency":"BTC",
                "quoteCurrency":"USDT",
                "quantity":"0.010000",
                "cumQuantity":"0.010000",
                "avgPx":"42645.422360",
                "lastPx":"42645.422360",
                "lastQty":"0.010000",
                "lastTurnover":"426.454223",
                "commission":"0 BTC",
                "transactionTime":1641959878075,
                "userId":11433212,
                "status":2,
                "symbolDisplayName":"BTCUSDT",
                "clearingStatus":0,
                "clearingAt":0,
                "clearingSourceId":"",
                "clearedQty":"0.000000",
                "clearedTurnover":"0.000000",
                "unClearedQty":"0.010000",
                "unClearedTurnover":"426.454223",
                "quantityPrecision":6,
                "amountPrecision":6
            }
        ],
        "total":2,
        "size":10,
        "page":1
    },
    "success":true,
    "messageArgs":[

    ]
}
```
### 響應數據


<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"><span style="white-space: pre-wrap">業務編碼</span></span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">錯誤消息</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> items</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">分頁數據</span></td>
     <td key="5"><p key="3"><span style="font-weight: '700'"></p></td>
    </tr>
    <tr key="0-2-0-0">
     <td key="0"><span style="padding-left: 40px"> id</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-1">
     <td key="0"><span style="padding-left: 40px"> orderId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-2">
     <td key="0"><span style="padding-left: 40px"> side</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">買賣方向 1-買BUY 2-賣-SELL</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-3">
     <td key="0"><span style="padding-left: 40px"> timeInForce</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易類型:GTC,IOC,FOK；詢價交易只有FOK</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-4">
     <td key="0"><span style="padding-left: 40px"> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">基礎幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-5">
     <td key="0"><span style="padding-left: 40px"> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">計價幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-6">
     <td key="0"><span style="padding-left: 40px"> quantity</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-7">
     <td key="0"><span style="padding-left: 40px"> cumQuantity</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">累計已交易訂單數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-8">
     <td key="0"><span style="padding-left: 40px"> avgPx</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">累計已交易訂單平均成交價格累</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-9">
     <td key="0"><span style="padding-left: 40px"> lastPx</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">本次交易價格</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-10">
     <td key="0"><span style="padding-left: 40px"> lastQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">本次交易數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-11">
     <td key="0"><span style="padding-left: 40px"> lastTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">本次交易金額=lastPx*lastQty</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-12">
     <td key="0"><span style="padding-left: 40px"> commission</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易手續費/佣金</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-13">
     <td key="0"><span style="padding-left: 40px"> transactionTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">時間戳</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-14">
     <td key="0"><span style="padding-left: 40px"> userId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">用戶id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-15">
     <td key="0"><span style="padding-left: 40px"> status</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單狀態:询价交易只有2-成功，4-取消，8-失敗</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-16">
     <td key="0"><span style="padding-left: 40px"> symbolDisplayName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易對展示名稱</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-17">
     <td key="0"><span style="padding-left: 40px"> clearingStatus</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">清算狀態(0, "待清算"|1, "成交自動清算"|2, "部分清算"|3, "已完成"|4, "清算失敗")</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-18">
     <td key="0"><span style="padding-left: 40px"> clearingAt</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">結算時間</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-19">
     <td key="0"><span style="padding-left: 40px"> clearingSourceId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">結算批次id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-20">
     <td key="0"><span style="padding-left: 40px"> clearedQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">已結算的數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-21">
     <td key="0"><span style="padding-left: 40px"> clearedTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">已結算的金額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-22">
     <td key="0"><span style="padding-left: 40px"> unClearedQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">待結算的數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-23">
     <td key="0"><span style="padding-left: 40px"> unClearedTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">待結算的金額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-24">
     <td key="0"><span style="padding-left: 40px"> quantityPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">數量精度 (base)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-25">
     <td key="0"><span style="padding-left: 40px"> amountPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">金额精度 (quote)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> total</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">總計數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">每頁數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">當前頁數</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table> 
 </body>
</html>

## 授信用戶提交結算

支持用戶單次提交多筆訂單進行結算，或單筆訂單進行部分結算<BR>1)如果提交多筆訂單進行結算，此時amount要求為空<br>
2)如果選中單筆訂單進行結算，此時進行部分結算
### HTTP 請求

- POST `/open/otc/api/clearing/manual/clearing`

API Key 權限：寫入<br>

限頻值：10次/1s<br>

| 參數名稱   | 是否必須 | 類型   | 備註                                                         | 默認值  | 其他信息
| ---------- | -------- | ------ | ------------------------------------------------------------ | ------ | -------- |
| tradeIds | true     | Intege | 成交Id列表 |        |          |
| amount | false     | string | 當用戶選擇單筆結算的時候，需要制定歸還的金額。如果選擇多筆結算，此時該選項為空 |        |          |




> Response:

```json
{"code":200,"message":"success","data":true,"success":true,"messageArgs":[]}
```

### 響應數據

| 參數名稱 | 是否必須 | 數據類型 | 備註     | 其他信息                                                     |
| -------- | -------- | -------- | -------- | ------------------------------------------------------------ |
| code         | true    | integer     | 狀態碼  | |
| message      | false   | string    | 錯誤描述（如有）| |
| data         | false   | object    | 業務數據 ||

## 獲取用戶結算歷史

該接口可以查詢到用戶的結算歷史


### HTTP 請求

- POST `/open/otc/api/clearing/history`

API Key 權限：讀取<br>

限频值：10次/1s<br>

<table>
  <thead class="ant-table-thead">
    <tr>
      <th key=name>參數名稱</th><th key=type>類型</th><th key=required>是否必須</th><th key=default>默認值</th><th key=desc>備註</th><th key=sub>其他信息</th>
    </tr>
  </thead><tbody className="ant-table-tbody"><tr key=0-0><td key=0><span style="padding-left: 0px"><span></span> page</span></td><td key=1><span>object</span></td><td key=2>true</td><td key=3></td><td key=4><span style="white-space: pre-wrap">分页查询参数</span></td><td key=5></td></tr><tr key=0-0-0><td key=0><span style="padding-left: 20px"><span >size</span></td><td key=1><span>integer</span></td><td key=2>true</td><td key=3></td><td key=4><span style="white-space: pre-wrap">分頁數量</span></td><td key=5></td></tr><tr key=0-0-3><td key=0><span style="padding-left: 20px"><span >page</span></td><td key=1><span>integer</span></td><td key=2>true</td><td key=3></td><td key=4><span style="white-space: pre-wrap">當前頁數</span></td><td key=5></td></tr><tr key=0-1><td key=0><span style="padding-left: 0px"><span ></span> startTime</span></td><td key=1><span>integer</span></td><td key=2>false</td><td key=3></td><td key=4><span style="white-space: pre-wrap">訂單時間-查詢開始時間</span></td><td key=5></td></tr><tr key=0-2><td key=0><span style="padding-left: 0px"><span ></span> endTime</span></td><td key=1><span>integer</span></td><td key=2>false</td><td key=3></td><td key=4><span style="white-space: pre-wrap">訂單時間-查詢結束時間</span></td><td key=5></td></tr>
               </tbody>
              </table>




> Response:

```json
{
    "code":200,
    "message":"success",
    "data":{
        "items":[
            {
                "id":212,
                "time":1642589918281,
                "tradeCount":1,
                "tradeSymbols":[
                    "BTCUSDT"
                ],
                "tradeSides":[
                    1
                ]
            },
            {
                "id":211,
                "time":1641960130626,
                "tradeCount":1,
                "tradeSymbols":[
                    "ETHUSDT"
                ],
                "tradeSides":[
                    1
                ]
            }         
        ],
        "total":16,
        "size":2,
        "page":1
    },
    "success":true,
    "messageArgs":[

    ]
}
```


### 響應數據

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">參數名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務編碼</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">消息</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> items</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4">分頁數據</td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-0">
     <td key="0"><span style="padding-left: 40px"> id</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-1">
     <td key="0"><span style="padding-left: 40px"> time</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">時間</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-2">
     <td key="0"><span style="padding-left: 40px"> tradeCount</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-3">
     <td key="0"><span style="padding-left: 40px"> tradeSymbols</span></td>
     <td key="1"><span>string []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易對</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-4">
     <td key="0"><span style="padding-left: 40px"> tradeSides</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易方向</span></td>
     <td key="5"></td>
    </tr>
     <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> total</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">總計數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">每頁數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">當前頁數</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>


## 獲取用戶結算記錄詳情

該接口支持守信用戶查詢結算記錄詳情

### HTTP 請求

- GET `/open/otc/api/clearing/details/{clearingId}`

API Key 权限：讀取<br>

限频值：10次/1秒<br>
### 請求參數

| 参数名稱 | 示例  | 備註  |
| ------------ | ------------ | ------------ |
| clearingId |   |   |

> Response:

```json
{
    "code": 200,
    "message": "success",
    "data": {
        "id": 212,
        "time": 1642589918281,
        "tradeCount": 1,
        "tradeSymbols": [
            "BTCUSDT"
        ],
        "tradeSides": [
            1
        ],
        "payouts": {
            "USDT": 23
        },
        "receivables": {
            "BTC": 0.000539
        },
        "trades": [
            {
                "tradeId": 2089,
                "time": 1641959878075,
                "symbol": "BTCUSDT",
                "baseCurrency": "BTC",
                "quoteCurrency": "USDT",
                "side": 1,
                "avgPx": 42645.422360010000000000,
                "cumQuantity": 0.010000000000000000,
                "cumTurnover": 426.454223600000000000,
                "clearedQty": 0.000539,
                "clearedTurnover": 23
            }
        ]
    },
    "success": true,
    "messageArgs": []
}
```

### 返回数据

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務編碼</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">消息</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> id</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">結算id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> time</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">結算時間</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> tradeCount</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">含有交易的筆數</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> tradeSymbols</span></td>
     <td key="1"><span>string []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">含有的交易對</span></td>
     <td key="5"></td>
    <tr key="0-2-4">
     <td key="0"><span style="padding-left: 20px"> tradeSides</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">含有的交易方向</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-5">
     <td key="0"><span style="padding-left: 20px"> payouts</span></td>
     <td key="1"><span>Map</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">應付</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-6">
     <td key="0"><span style="padding-left: 20px"> receivables</span></td>
     <td key="1"><span>Map</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">應收</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7">
     <td key="0"><span style="padding-left: 20px"> trades</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易记录</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-0">
     <td key="0"><span style="padding-left: 40px"> tradeId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-1">
     <td key="0"><span style="padding-left: 40px"> time</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">成交時間</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-2">
     <td key="0"><span style="padding-left: 40px"> symbol</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易對</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-3">
     <td key="0"><span style="padding-left: 40px"> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">基礎幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-4">
     <td key="0"><span style="padding-left: 40px"> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">計價币种</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-5">
     <td key="0"><span style="padding-left: 40px"> side</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">買賣方向 1-買BUY 2-賣-SELL</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-6">
     <td key="0"><span style="padding-left: 40px"> avgPx</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">成交價</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-7">
     <td key="0"><span style="padding-left: 40px"> cumQuantity</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">成交數</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-8">
     <td key="0"><span style="padding-left: 40px"> cumTurnover</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">成交額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-9">
     <td key="0"><span style="padding-left: 40px"> clearedQty</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">本次結算數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7-10">
     <td key="0"><span style="padding-left: 40px"> clearedTurnover</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">本次結算金額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table> 
 </body>
</html>

## 获取用户授信汇总信息
用戶可以通過該接口查詢到自己賬戶的授信匯總信息

### HTTP 請求

- GET `/open/otc/api/clearing/query-account-summary`

API Key 權限：讀取<br>

限頻值：10次/1s<br>
### 請求參數

> Response:

```json
{
    "code":200,
    "message":"success",
    "data":{
        "totalCredit":"20000000.00",
        "spentCredit":"1051.09",
        "availableCredit":"19998948.90",
        "payouts":[
            {
                "id":"USDT",
                "currency":"USDT",
                "amount":403.4542236,
                "total":"403.45"
            },
            {
                "id":"HUSD",
                "currency":"HUSD",
                "amount":647.642482,
                "total":"647.64"
            }
        ]
    },
    "success":true,
    "messageArgs":[

    ]
}
```
### 返回数据

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"</span> 業務編碼 </td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">消息</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> totalCredit</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">授信總額度</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> spentCredit</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">已使用授信總額度</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> availableCredit</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">可用授信額度</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> payouts</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">应還幣種信息</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3-0">
     <td key="0"><span style="padding-left: 40px"> id</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3-1">
     <td key="0"><span style="padding-left: 40px"> currency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3-2">
     <td key="0"><span style="padding-left: 40px"> amount</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">應還金額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3-3">
     <td key="0"><span style="padding-left: 40px"> total</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">折合USD金額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table> 
 </body>
</html> 

# 用戶賬戶相關

## 獲取用戶資產信息
用戶可以通過該接口查詢自己賬戶的資產信息

### HTTP 請求

- GET `/open/otc/api/user/accountSummary`

API Key 權限：讀取<br>

限頻值：10次/1s<br>
### 請求參數

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":{
    "financeAccounts":[
      {
        "currencyId":"usd",
        "currencyDisplayName":"USD",
        "currencyFullName":"USD",
        "sortWeight":8,
        "balance":"6929.280000000000000000",
        "frozenAmount":"1893.750000000000000000",
        "creditedAmount":"0",
        "receivableAmount":"0",
        "virtualFrozenAmount":null,
        "withdrawAmount":null,
        "balanceToPlaceOrder":null,
        "stable":"false",
        "inCurrencyBlackList":false,
        "spotBalance":null
      },
      {
        "currencyId":"btc",
        "currencyDisplayName":"BTC",
        "currencyFullName":"BTC",
        "sortWeight":1,
        "balance":"0.020000000000000000",
        "frozenAmount":"0.000000000000000000",
        "creditedAmount":"0",
        "receivableAmount":"0.000000000000000000",
        "virtualFrozenAmount":null,
        "withdrawAmount":null,
        "balanceToPlaceOrder":null,
        "stable":"false",
        "inCurrencyBlackList":false,
        "spotBalance":null
      },
      {
        "currencyId":"usdt",
        "currencyDisplayName":"USDT",
        "currencyFullName":"USDT",
        "sortWeight":1,
        "balance":"2941.033920000000000000",
        "frozenAmount":"4100.000000000000000000",
        "creditedAmount":"0",
        "receivableAmount":"0.000000000000000000",
        "virtualFrozenAmount":null,
        "withdrawAmount":null,
        "balanceToPlaceOrder":null,
        "stable":"false",
        "inCurrencyBlackList":false,
        "spotBalance":null
      }
    ],
    "totalDigitalCurrency":"BTC",
    "totalConvertedDigitalCurrencyBalance":"0.39445219",
    "sumLegalCurrency":"USD",
    "sumConvertedLegalCurrencyBalance":"16711.38512000",
    "sumLegalCurrencyBalance":"8823.03000000",
    "totalLegalCurrencyBalance":"0.20825703",
    "sumDigitalCurrencyBalance":"7888.35512000",
    "totalDigitalCurrencyBalance":"0.18619516",
    "defaultCreditCategory":false,
    "unstableCreditLimit":null,
    "unstableCreditUsed":null,
    "unstableCreditUsedWithoutLocked":null,
    "unstableCreditAvailable":null,
    "unstableCreditCurrencyDisplay":null
  },
  "success":true,
  "messageArgs":[

  ]
}
```
### 返回数据

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務狀態碼</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">錯誤信息（英文）</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> financeAccounts</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">賬戶列表</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-0">
     <td key="0"><span style="padding-left: 40px"> currencyId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">幣種ID</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-1">
     <td key="0"><span style="padding-left: 40px"> currencyDisplayName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">幣種展示名稱</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-2">
     <td key="0"><span style="padding-left: 40px"> currencyFullName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">幣種全稱</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-3">
     <td key="0"><span style="padding-left: 40px"> sortWeight</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">排序權重</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-4">
     <td key="0"><span style="padding-left: 40px"> balance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">餘額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-5">
     <td key="0"><span style="padding-left: 40px"> frozenAmount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">凍結金額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-6">
     <td key="0"><span style="padding-left: 40px"> creditedAmount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">已使用授信</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-7">
     <td key="0"><span style="padding-left: 40px"> receivableAmount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">應收金額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-8">
     <td key="0"><span style="padding-left: 40px"> virtualFrozenAmount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">授信已凍結</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-9">
     <td key="0"><span style="padding-left: 40px"> withdrawAmount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">可劃轉餘額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-10">
     <td key="0"><span style="padding-left: 40px"> balanceToPlaceOrder</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">下單可用=賬戶餘額 + 應收</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-11">
     <td key="0"><span style="padding-left: 40px"> stable</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否為穩定幣， true or false</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-12">
     <td key="0"><span style="padding-left: 40px"> inCurrencyBlackList</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">用戶所在國際是否在該幣種的國籍黑名單中</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-13">
     <td key="0"><span style="padding-left: 40px"> spotBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">幣幣賬戶餘額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> totalDigitalCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">總資產幣種(數字幣)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> totalConvertedDigitalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">總資產（數字幣折算BTC）</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> sumLegalCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">總資產(法幣)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-4">
     <td key="0"><span style="padding-left: 20px"> sumConvertedLegalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">總資產（法幣折算）</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-5">
     <td key="0"><span style="padding-left: 20px"> sumLegalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">法幣總資產</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-6">
     <td key="0"><span style="padding-left: 20px"> totalLegalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">法幣總資產（法幣折算BTC）</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7">
     <td key="0"><span style="padding-left: 20px"> sumDigitalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">數字幣總資產</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-8">
     <td key="0"><span style="padding-left: 20px"> totalDigitalCurrencyBalance</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">數字幣總資產（数字币折算BTC）</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-9">
     <td key="0"><span style="padding-left: 20px"> defaultCreditCategory</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">默認授信級別</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-10">
     <td key="0"><span style="padding-left: 20px"> unstableCreditLimit</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">非穩定幣限額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-11">
     <td key="0"><span style="padding-left: 20px"> unstableCreditUsed</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">非穩定幣已使用授信額度</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-12">
     <td key="0"><span style="padding-left: 20px"> unstableCreditUsedWithoutLocked</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">非穩定幣已使用授信額度</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-13">
     <td key="0"><span style="padding-left: 20px"> unstableCreditAvailable</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">非穩定幣授信可用</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-14">
     <td key="0"><span style="padding-left: 20px"> unstableCreditCurrencyDisplay</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">非穩定幣顯示名稱</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

# 幣種、交易對相關

## 獲取全部上線幣種
用戶可以通過該接口查詢到已上線的全部幣種

### HTTP 請求

- GET `/open/otc/api/currency/queryCurrency`

API Key 權限：讀取<br>

限頻值：10次/1s<br>
### 請求參數

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":[
    {
      "currencyId":"eth",
      "fullName":"ETH_2",
      "amountPrecision":4,
      "type":null,
      "currencyType":0
    },
    {
      "currencyId":"gbp",
      "fullName":"GBP",
      "amountPrecision":2,
      "type":null,
      "currencyType":1
    },
    {
      "currencyId":"btc",
      "fullName":"BTC",
      "amountPrecision":8,
      "type":null,
      "currencyType":0
    },
    {
      "currencyId":"usdt",
      "fullName":"USDT",
      "amountPrecision":8,
      "type":null,
      "currencyType":0
    }
  ],
  "success":true,
  "messageArgs":[

  ]
}
```
### 返回数据
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必须</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務狀態碼</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必须</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">錯誤信息</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必须</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> currencyId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必须</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">币幣種ID，幣種標識, 小写 btc</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px">fullName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必须</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">币种全称， Bitcoin</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> amountPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必须</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">金額前端展示精度</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必须</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必须</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

## 獲取全部上線交易對
用戶可以通過該接口查詢到已上線的全部交易對

### HTTP 請求

- GET `/open/otc/api/symbol`

API Key 權限：讀取<br>

限頻值：10次/1s<br>
### 請求參數

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":[
    {
      "symbol":"btcusdt",
      "baseCurrency":"BTC",
      "quoteCurrency":"USDT",
      "pricePrecision":6,
      "quantityPrecision":6,
      "amountPrecision":6,
      "fokEligible":1,
      "iocEligible":0,
      "gtcEligible":0
    },
    {
      "symbol":"ethusd",
      "baseCurrency":"ETH",
      "quoteCurrency":"USD",
      "pricePrecision":8,
      "quantityPrecision":8,
      "amountPrecision":8,
      "fokEligible":1,
      "iocEligible":0,
      "gtcEligible":0
    }
  ],
  "success":true,
  "messageArgs":[

  ]
}
```
### 返回数据
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務狀態碼</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">錯誤信息（英文）</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> symbol</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易對id, 例如 btcusdt</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">基礎幣種，例如 BTC</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">計價幣種，例如 USDT</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> pricePrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易對 下單價格精度</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-4">
     <td key="0"><span style="padding-left: 20px"> quantityPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易對 下單數量精度</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-5">
     <td key="0"><span style="padding-left: 20px"> amountPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易對 下單金額精度</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-6">
     <td key="0"><span style="padding-left: 20px"> fokEligible</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">支持fok標誌，1支持，0不支持</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-7">
     <td key="0"><span style="padding-left: 20px"> iocEligible</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">支持ioc標誌，1支持，0不支持</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-8">
     <td key="0"><span style="padding-left: 20px"> gtcEligible</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">支持gtc標誌，1支持，0不支持</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

## 獲取交易對規則
用戶可以通過該接口查詢到交易對規則

### HTTP 請求

- GET `/open/otc/api/symbol/{symbol}/setting`

API Key 權限：讀取<br>

限頻值：10次/1s<br>
### 請求參數

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":[
    {
      "symbol":"btcusdt",
      "ruleName":"FOK_AMOUNT",
      "ruleType":"MIN_VALUE",
      "ruleValue":"0.01"
    },
    {
      "symbol":"btcusdt",
      "ruleName":"FOK_QUANTITY",
      "ruleType":"MAX_VALUE",
      "ruleValue":"10"
    },
    {
      "symbol":"btcusdt",
      "ruleName":"FOK_QUANTITY",
      "ruleType":"MIN_VALUE",
      "ruleValue":"0.01"
    },
    {
      "symbol":"btcusdt",
      "ruleName":"FOK_AMOUNT",
      "ruleType":"MAX_VALUE",
      "ruleValue":"1000"
    }
  ],
  "success":true,
  "messageArgs":[

  ]
}
```
### 返回数据
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">业务狀態码</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">錯誤信息（英文）</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> symbol</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易對id，小写, 例如 btcusdt</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> ruleName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">規則名稱</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> ruleType</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">規則子類型</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> ruleValue</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">規則值</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>


# 询价交易

## 发起询价请求
用戶可以通過該接口發起詢價請求

### HTTP 請求

- POST `/open/otc/api/order/rfq/quote/request`

API Key 權限：讀取<br>

限頻值：10次/1s<br>

請求參數

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">基礎幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">計價幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> side</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">買賣方向 1-買BUY 2-賣-SELL</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> baseCurrencySize</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">基礎幣種数值 (null或大于0的數值) 注：基礎幣種数值和計價幣種数值不能并存。 RFQ下單方式有兩種，只能取其一： a) 按baseCurrency數量下單 b) 按quoteCurrency金额下單</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> quoteCurrencySize</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">計價幣種数值(null或大于0的数值) 注：基礎幣種数值和計價幣種数值不能并存。 RFQ下單方式有两种，只能取其一： a) 按baseCurrency數量下單 b) 按quoteCurrency金额下單 （同時有baseCurrencySize優先用baseCurrencySize）</span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":{
    "requestId":"98cdbcfbce2e7ff7d14786a1c8ed409040a1e9f1",
    "price":41944.861407,
    "timestamp":1642658651145
  },
  "success":true,
  "messageArgs":[

  ]
}
```
### 響應數據

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務狀態碼</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">錯誤信息</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> requestId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">詢價業務號</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> price</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">詢價價格</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> timestamp</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">時間戳</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>



## 发起鎖價下單请求
用戶可以通過該接口發起鎖價下單請求

### HTTP 請求

- POST `/open/otc/api/order/rfq/quote/accept`

API Key 權限：寫入<br>

限頻值：10次/1s<br>

### 請求參數
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> rfqQuotationId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">詢價返回的業務號（6分鐘內有效）</span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table> 
 </body>
</html>

> Response:

```json
{"code":200,"message":"success","data":1459564954255424,"success":true,"messageArgs":[]}
```
### 響應數據

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務狀態碼</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">錯誤信息</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

## 獲取用戶所有成交記錄
用戶可以通過該接口獲取訂單成交記錄

### HTTP 請求

- POST `/open/otc/api/order/rfq/query`

API Key 權限：讀取<br>

限頻值：10次/1s<br>
### 請求參數
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> page</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">分页查询参数</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-0-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">每頁數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-0-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">當前頁數</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> side</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">買賣方向 1-買BUY 2-賣-SELL</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">基礎幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">計價幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> timeInForce</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"></span>交易類型:目前只支持FOK<BR>
    GTC(1): 委托订单，可部分成交，持续挂单直到用户提交撤销指令。<BR>
    IOC(3):立即成交，可部分成交，剩余部分撤销。<BR>
    FOK(4):立即成交，全部成交或全部撤销。<BR>
    </td>
     <td key="5"></td>
    </tr>
    <tr key="0-5">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> startTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單时间查询开始时间</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-6">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> endTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單时间-查询结束时间</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-7">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> orderId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-8">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> clearingStatus</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">清算狀態(0, "待清算"|1, "成交自動清算"|2, "部分清算"|3, "已完成"|4, "清算失敗")</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-9">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> tradeStatusList</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易狀態集合</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-10">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> clearingStatusList</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">清算狀態集合 (0, "待清算"|1, "成交自動清算"|2, "部分清算"|3, "已完成"|4, "清算失敗")</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-11">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> ascending</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">正序(&quot;asc&quot;)还是倒序(&quot;desc&quot;)，默认是倒序</span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table> 
 </body>
</html>

> Response:

```json
{
  "code":200,
  "message":"success",
  "data":{
    "items":[
      {
        "id":2107,
        "orderId":1459028660060224,
        "side":2,
        "timeInForce":4,
        "baseCurrency":"BTC",
        "quoteCurrency":"USDT",
        "quantity":"0.010000",
        "cumQuantity":"0.010000",
        "avgPx":"42763.112689",
        "lastPx":"42763.112689",
        "lastQty":"0.010000",
        "lastTurnover":"427.631127",
        "commission":"0 USDT",
        "transactionTime":1642403881442,
        "userId":11433560,
        "status":"2",
        "symbolDisplayName":"BTCUSDT",
        "clearingStatus":1,
        "clearingAt":1642403881442,
        "clearingSourceId":"",
        "clearedQty":"0.010000",
        "clearedTurnover":"427.631127",
        "unClearedQty":"0.000000",
        "unClearedTurnover":"0.000000",
        "quantityPrecision":6,
        "amountPrecision":6
      },
      {
        "id":2105,
        "orderId":1459028332904512,
        "side":1,
        "timeInForce":4,
        "baseCurrency":"BTC",
        "quoteCurrency":"USDT",
        "quantity":"0.010000",
        "cumQuantity":"0.010000",
        "avgPx":"42876.586450",
        "lastPx":"42876.586450",
        "lastQty":"0.010000",
        "lastTurnover":"428.765864",
        "commission":"0 BTC",
        "transactionTime":1642403724601,
        "userId":11433560,
        "status":"2",
        "symbolDisplayName":"BTCUSDT",
        "clearingStatus":1,
        "clearingAt":1642403724601,
        "clearingSourceId":"",
        "clearedQty":"0.010000",
        "clearedTurnover":"428.765864",
        "unClearedQty":"0.000000",
        "unClearedTurnover":"0.000000",
        "quantityPrecision":6,
        "amountPrecision":6
      }
    ],
    "total":2,
    "size":10,
    "page":1
  },
  "success":true,
  "messageArgs":[

  ]
}
```
### 響應數據

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務狀態碼</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">錯誤信息</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> items</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">分頁數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-0">
     <td key="0"><span style="padding-left: 40px"> id</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-1">
     <td key="0"><span style="padding-left: 40px"> orderId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單ID</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-2">
     <td key="0"><span style="padding-left: 40px"> side</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">買賣方向 1-買BUY 2-賣-SELL</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-3">
     <td key="0"><span style="padding-left: 40px"> timeInForce</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"></span>交易類型:目前只支持FOK<BR>
    GTC(1): 委托订单，可部分成交，持续挂单直到用户提交撤销指令。<BR>
    IOC(3):立即成交，可部分成交，剩余部分撤销。<BR>
    FOK(4):立即成交，全部成交或全部撤销。<BR>
     </td>     <td key="5"></td>
    </tr>
    <tr key="0-2-0-4">
     <td key="0"><span style="padding-left: 40px"> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">基礎幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-5">
     <td key="0"><span style="padding-left: 40px"> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">計價幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-6">
     <td key="0"><span style="padding-left: 40px"> quantity</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-7">
     <td key="0"><span style="padding-left: 40px"> cumQuantity</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">累计已交易訂單數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-8">
     <td key="0"><span style="padding-left: 40px"> avgPx</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">累计已交易訂單平均成交價格</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-9">
     <td key="0"><span style="padding-left: 40px"> lastPx</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">本次交易價格</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-10">
     <td key="0"><span style="padding-left: 40px"> lastQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">本次交易數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-11">
     <td key="0"><span style="padding-left: 40px"> lastTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">本次交易金额 =lastPx*lastQty</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-12">
     <td key="0"><span style="padding-left: 40px"> commission</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易手續費/佣金</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-13">
     <td key="0"><span style="padding-left: 40px"> transactionTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">时间戳</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-14">
     <td key="0"><span style="padding-left: 40px"> userId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">用戶id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-15">
     <td key="0"><span style="padding-left: 40px"> status</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單狀態 询价交易只有2-成功，4-取消，8-失敗</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-16">
     <td key="0"><span style="padding-left: 40px"> symbolDisplayName</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易對展示名稱</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-17">
     <td key="0"><span style="padding-left: 40px"> clearingStatus</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">清算狀態(0, "待清算"|1, "成交自動清算"|2, "部分清算"|3, "已完成"|4, "清算失敗")</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-18">
     <td key="0"><span style="padding-left: 40px"> clearingAt</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">結算时间</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-19">
     <td key="0"><span style="padding-left: 40px"> clearingSourceId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">結算批次ID</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-20">
     <td key="0"><span style="padding-left: 40px"> clearedQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">已結算的數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-21">
     <td key="0"><span style="padding-left: 40px"> clearedTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">已結算的金额</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-22">
     <td key="0"><span style="padding-left: 40px"> unClearedQty</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">待結算的數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-23">
     <td key="0"><span style="padding-left: 40px"> unClearedTurnover</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">待結算的金额</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-24">
     <td key="0"><span style="padding-left: 40px"> quantityPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">數量精度 (base)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-25">
     <td key="0"><span style="padding-left: 40px"> amountPrecision</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">金额精度 (quote)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> total</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">總頁數</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">每頁數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">當前頁數</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

## 獲取用戶歷史訂單
用戶可以通過該接口獲取歷史訂單

### HTTP 請求

- POST `/open/otc/api/order/rfq/queryHistoryOrder`

API Key 權限：讀取<br>

限頻值：10次/1s<br>
### 請求參數

<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> page</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">分頁查询参数</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-0-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">每頁數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-0-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">當前頁數</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> side</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">買賣方向 1-買BUY 2-賣-SELL</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> export</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">非必須</td>
     <td key="3">false</td>
     <td key="4"><span style="white-space: pre-wrap"></span>是否導出</td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">基礎幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">計價幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-5">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> excludeCancelled</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否排除已撤销訂單 「已废弃」</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-6">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> orderId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單ID</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-7">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> startTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單时-查詢開始時間</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-8">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> endTime</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單时间-查詢結束時間</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-9">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> orderStateList</span></td>
     <td key="1"><span>integer []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">询价交易只有2-成功，4-取消，8-失敗</span></td>
     <td key="5"></td>
    </tr>
   </tbody> 
  </table> 
 </body>
</html>
> Response:

```json
{
  "code":200,
  "message":"success",
  "data":{
    "items":[
      {
        "orderId":1459028660060224,
        "userId":11433560,
        "timeInForce":4,
        "symbol":"BTCUSDT",
        "baseCurrency":"BTC",
        "quoteCurrency":"USDT",
        "side":2,
        "cumTurnover":427.631127,
        "quantity":0.01,
        "price":42763.112689,
        "createAt":1642403880381,
        "lastQty":0.01,
        "lastPx":42763.112689,
        "cumQuantity":0.01,
        "avgPx":42763.112689,
        "commissionFee":0,
        "updatedAt":1642403881488,
        "status":2,
        "clOrdId":"1459028660060192",
        "orderType":null,
        "source":1,
        "accountOperateType":1,
        "amount":"427.631126",
        "unComQuantity":"0.000000",
        "quantityStr":"0.010000",
        "priceStr":"42763.112689",
        "comQuantityStr":"0.010000",
        "avgPxStr":"42763.112689",
        "commissionFeeStr":null,
        "sideStr":null,
        "timeInForceStr":null,
        "statusStr":null,
        "orderIdStr":"1459028660060224"
      },
      {
        "orderId":1459028332904512,
        "userId":11433560,
        "timeInForce":4,
        "symbol":"BTCUSDT",
        "baseCurrency":"BTC",
        "quoteCurrency":"USDT",
        "side":1,
        "cumTurnover":428.765864,
        "quantity":0.01,
        "price":42876.58645,
        "createAt":1642403724093,
        "lastQty":0.01,
        "lastPx":42876.58645,
        "cumQuantity":0.01,
        "avgPx":42876.58645,
        "commissionFee":0,
        "updatedAt":1642403724650,
        "status":2,
        "clOrdId":"1459028332904480",
        "orderType":null,
        "source":1,
        "accountOperateType":1,
        "amount":"428.765864",
        "unComQuantity":"0.000000",
        "quantityStr":"0.010000",
        "priceStr":"42876.586450",
        "comQuantityStr":"0.010000",
        "avgPxStr":"42876.586450",
        "commissionFeeStr":null,
        "sideStr":null,
        "timeInForceStr":null,
        "statusStr":null,
        "orderIdStr":"1459028332904512"
      }
    ],
    "total":2,
    "size":10,
    "page":1
  },
  "success":true,
  "messageArgs":[

  ]
}
```
### 響應數據
<html>
 <head></head>
 <body>
  <table> 
   <thead class="ant-table-thead"> 
    <tr> 
     <th key="name">名稱</th>
     <th key="type">類型</th>
     <th key="required">是否必須</th>
     <th key="default">默認值</th>
     <th key="desc">備註</th>
     <th key="sub">其他信息</th> 
    </tr> 
   </thead>
   <tbody classname="ant-table-tbody">
    <tr key="0-0">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> code</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap"></span>業務狀態碼</td>
     <td key="5"></td>
    </tr>
    <tr key="0-1">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> message</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">錯誤消息</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> data</span></td>
     <td key="1"><span>object</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">業務數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0">
     <td key="0"><span style="padding-left: 20px"> items</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">分頁數據</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-0">
     <td key="0"><span style="padding-left: 40px"> orderId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">*訂單id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-1">
     <td key="0"><span style="padding-left: 40px"> userId</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">用戶id</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-2">
     <td key="0"><span style="padding-left: 40px"> timeInForce</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">GTC,IOC,FOK；詢價交易只有FOK</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-3">
     <td key="0"><span style="padding-left: 40px"> symbol</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易對</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-4">
     <td key="0"><span style="padding-left: 40px"> baseCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">基礎幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-5">
     <td key="0"><span style="padding-left: 40px"> quoteCurrency</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">計價幣種</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-6">
     <td key="0"><span style="padding-left: 40px"> side</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">買賣方向 1-買BUY 2-賣-SELL</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-7">
     <td key="0"><span style="padding-left: 40px"> cumTurnover</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">累計營業額</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-8">
     <td key="0"><span style="padding-left: 40px"> quantity</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-9">
     <td key="0"><span style="padding-left: 40px"> price</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">價格</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-10">
     <td key="0"><span style="padding-left: 40px"> createAt</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">創建時間</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-11">
     <td key="0"><span style="padding-left: 40px"> lastQty</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">最近一笔成交數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-12">
     <td key="0"><span style="padding-left: 40px"> lastPx</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">最近一笔成交的價格</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-13">
     <td key="0"><span style="padding-left: 40px"> cumQuantity</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">base currency 累计成交數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-14">
     <td key="0"><span style="padding-left: 40px"> avgPx</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單平均成交價格</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-15">
     <td key="0"><span style="padding-left: 40px"> commissionFee</span></td>
     <td key="1"><span>BigDecimal</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">費率</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-16">
     <td key="0"><span style="padding-left: 40px"> updatedAt</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">更新時間</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-17">
     <td key="0"><span style="padding-left: 40px"> status</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單狀態 询价交易只有2-成功，4-拒绝，8-失败</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-18">
     <td key="0"><span style="padding-left: 40px"> clOrdId</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">用户OrderId， 下單</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-19">
     <td key="0"><span style="padding-left: 40px"> orderType</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單類型:废弃字段</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-20">
     <td key="0"><span style="padding-left: 40px"> source</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">订单来源(0: API下单 1: 页面下单(WEB) 2: MGT下单 3: 流动性反向订单下单)</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-21">
     <td key="0"><span style="padding-left: 40px"> accountOperateType</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">下單时使用的账户類型</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-22">
     <td key="0"><span style="padding-left: 40px"> amount</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單金额</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-23">
     <td key="0"><span style="padding-left: 40px"> unComQuantity</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">*未完成數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-24">
     <td key="0"><span style="padding-left: 40px"> quantityStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-25">
     <td key="0"><span style="padding-left: 40px"> priceStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">價格</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-26">
     <td key="0"><span style="padding-left: 40px"> comQuantityStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單已成交數量</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-27">
     <td key="0"><span style="padding-left: 40px"> avgPxStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單平均成交價格</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-28">
     <td key="0"><span style="padding-left: 40px"> commissionFeeStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">费率</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-29">
     <td key="0"><span style="padding-left: 40px"> sideStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">交易方向</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-30">
     <td key="0"><span style="padding-left: 40px"> timeInForceStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">GTC,IOC,FOK；询价交易只有FOK</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-31">
     <td key="0"><span style="padding-left: 40px"> statusStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">訂單狀態 询价交易只有2-成功，4-取消，8-失败</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-0-32">
     <td key="0"><span style="padding-left: 40px"> orderIdStr</span></td>
     <td key="1"><span>string</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">orderID</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-1">
     <td key="0"><span style="padding-left: 20px"> total</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">總頁數.</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-2">
     <td key="0"><span style="padding-left: 20px"> size</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">每頁數量.</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-2-3">
     <td key="0"><span style="padding-left: 20px"> page</span></td>
     <td key="1"><span>integer</span></td>
     <td key="2">非必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">當前頁數</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-3">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> success</span></td>
     <td key="1"><span>boolean</span></td>
     <td key="2">必須</td>
     <td key="3"></td>
     <td key="4"><span style="white-space: pre-wrap">是否成功</span></td>
     <td key="5"></td>
    </tr>
    <tr key="0-4">
     <td key="0"><span style="padding-left: 0px"><span style="color: #8c8a8a"></span> messageArgs</span></td>
     <td key="1"><span>object []</span></td>
     <td key="2">非必須</td>
     <td key="3">new ArrayList&lt;&gt;()</td>
     <td key="4"><span style="white-space: pre-wrap"></span></td>
     <td key="5"></td>
    </tr> 
   </tbody> 
  </table>
 </body>
</html>

  
  
