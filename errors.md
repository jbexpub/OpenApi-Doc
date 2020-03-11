# Errors

Errors consist of two parts: an error code and a message. Codes are universal, but messages can vary. Here is the error JSON payload:

```javascript
{
  "code":-1121,
  "msg":"Invalid symbol."
}
```

## 10xx - General Server or Network issues

### -1000 UNKNOWN

* An unknown error occured while processing the request.

### -1001 DISCONNECTED

* Internal error; unable to process your request. Please try again.

### -1002 UNAUTHORIZED

* You are not authorized to execute this request. Request need API Key included in . We suggest that API Key be included in any request.

### -1003 TOO\_MANY\_REQUESTS

* Too many requests; please use the websocket for live updates.
* Too many requests; current limit is %s requests per minute. Please use the websocket for live updates to avoid polling the API.
* Way too many requests; IP banned until %s. Please use the websocket for live updates to avoid bans.

### -1006 UNEXPECTED\_RESP

* An unexpected response was received from the message bus. Execution status unknown. OPEN API server find some exception in execute request .Please report to Customer service.

### -1007 TIMEOUT

* Timeout waiting for response from backend server. Send status unknown; execution status unknown.

### -1014 UNKNOWN\_ORDER\_COMPOSITION

* Unsupported order combination.

### -1015 TOO\_MANY\_ORDERS

* Reach the rate limit .Please slow down your request speed.
* Too many new orders.
* Too many new orders; current limit is %s orders per %s.

### -1016 SERVICE\_SHUTTING\_DOWN

* This service is no longer available.

### -1020 UNSUPPORTED\_OPERATION

* This operation is not supported.

### -1021 INVALID\_TIMESTAMP

* Timestamp for this request is outside of the recvWindow.
* Timestamp for this request was 1000ms ahead of the server's time.
* Please check the difference between your local time and server time .

### -1022 INVALID\_SIGNATURE

* Signature for this request is not valid.

## 11xx - Request issues

### -1100 ILLEGAL\_CHARS

* Illegal characters found in a parameter.
* Illegal characters found in parameter '%s'; legal range is '%s'.

### -1101 TOO\_MANY\_PARAMETERS

* Too many parameters sent for this endpoint.
* Too many parameters; expected '%s' and received '%s'.
* Duplicate values for a parameter detected.

### -1102 MANDATORY\_PARAM\_EMPTY\_OR\_MALFORMED

* A mandatory parameter was not sent, was empty/null, or malformed.
* Mandatory parameter '%s' was not sent, was empty/null, or malformed.
* Param '%s' or '%s' must be sent, but both were empty/null!

### -1103 UNKNOWN\_PARAM

* An unknown parameter was sent.
* In JBEx Open Api , each request requires at least one parameter. {Timestamp}.

### -1104 UNREAD\_PARAMETERS

* Not all sent parameters were read.
* Not all sent parameters were read; read '%s' parameter\(s\) but was sent '%s'.

### -1105 PARAM\_EMPTY

* A parameter was empty.
* Parameter '%s' was empty.

### -1106 PARAM\_NOT\_REQUIRED

* A parameter was sent when not required.
* Parameter '%s' sent when not required.

### -1111 BAD\_PRECISION

* Precision is over the maximum defined for this asset.

### -1112 NO\_DEPTH

* No orders on book for symbol.

### -1114 TIF\_NOT\_REQUIRED

* TimeInForce parameter sent when not required.

### -1115 INVALID\_TIF

* Invalid timeInForce.
* In the current version, this parameter is either empty or GTC.

### -1116 INVALID\_ORDER\_TYPE

* Invalid orderType.
* In the current version , ORDER\_TYPE values is LIMIT or MARKET.

### -1117 INVALID\_SIDE

* Invalid side.
* ORDER\_SIDE values is BUY or SELL

### -1118 EMPTY\_NEW\_CL\_ORD\_ID

* New client order ID was empty.

### -1119 EMPTY\_ORG\_CL\_ORD\_ID

* Original client order ID was empty.

### -1120 BAD\_INTERVAL

* Invalid interval.

### -1121 BAD\_SYMBOL

* Invalid symbol.

### -1125 INVALID\_LISTEN\_KEY

* This listenKey does not exist.

### -1127 MORE\_THAN\_XX\_HOURS

* Lookup interval is too big.
* More than %s hours between startTime and endTime.

### -1128 OPTIONAL\_PARAMS\_BAD\_COMBO

* Combination of optional parameters invalid.

### -1130 INVALID\_PARAMETER

* Invalid data sent for a parameter.
* Data sent for paramter '%s' is not valid.

### -1132 ORDER\_PRICE\_TOO\_HIGH

* Order price too high.

### -1133 ORDER\_PRICE\_TOO\_SMALL

* Order price lower than the minimum,please check general broker info.

### -1134 ORDER\_PRICE\_PRECISION\_TOO\_LONG

* Order price decimal too long,please check general broker info.

### -1135 ORDER\_QUANTITY\_TOO\_BIG

* Order quantity too large.

### -1136 ORDER\_QUANTITY\_TOO\_SMALL

* Order quantity lower than the minimum.

### -1137 ORDER\_QUANTITY\_PRECISION\_TOO\_LONG

* Order quantity decimal too long.

### -1138 ORDER\_PRICE\_WAVE\_EXCEED

* Order price exceeds permissible range.

### -1139 ORDER\_HAS\_FILLED

* Order has been filled.

### -1140 ORDER\_AMOUNT\_TOO\_SMALL

* Transaction amount lower than the minimum.

### -1141 ORDER\_DUPLICATED

* Duplicate clientOrderId

### -1142 ORDER\_CANCELLED

* Order has been canceled

### -1143 ORDER\_NOT\_FOUND\_ON\_ORDER\_BOOK

* Cannot be found on order book

### -1144 ORDER\_LOCKED

* Order has been locked

### -1145 ORDER\_NOT\_SUPPORT\_CANCELLATION

* This order type does not support cancellation

### -1146 ORDER\_CREATION\_TIMEOUT

* Order creation timeout

### -1147 ORDER\_CANCELLATION\_TIMEOUT

* Order cancellation timeout

### -2010 NEW\_ORDER\_REJECTED

* NEW\_ORDER\_REJECTED

### -2011 CANCEL\_REJECTED

* CANCEL\_REJECTED

### -2013 NO\_SUCH\_ORDER

* Order does not exist.

### -2014 BAD\_API\_KEY\_FMT

* API-key format invalid.

### -2015 REJECTED\_MBX\_KEY

* Invalid API-key, IP, or permissions for action.

### -2016 NO\_TRADING\_WINDOW

* No trading window could be found for the symbol. Try ticker/24hrs instead.

## Messages for -1010 ERROR\_MSG\_RECEIVED, -2010 NEW\_ORDER\_REJECTED, and -2011 CANCEL\_REJECTED

This code is sent when an error has been returned by the matching engine. The following messages which will indicate the specific error:

| Error message | Description |
| :--- | :--- |
| "Unknown order sent." | The order \(by either `orderId`, `clOrdId`, `origClOrdId`\) could not be found |
| "Duplicate order sent." | The `clOrdId` is already in use |
| "Market is closed." | The symbol is not trading |
| "Account has insufficient balance for requested action." | Not enough funds to complete the action |
| "Market orders are not supported for this symbol." | `MARKET` is not enabled on the symbol |
| "Iceberg orders are not supported for this symbol." | `icebergQty` is not enabled on the symbol |
| "Stop loss orders are not supported for this symbol." | `STOP_LOSS` is not enabled on the symbol |
| "Stop loss limit orders are not supported for this symbol." | `STOP_LOSS_LIMIT` is not enabled on the symbol |
| "Take profit orders are not supported for this symbol." | `TAKE_PROFIT` is not enabled on the symbol |
| "Take profit limit orders are not supported for this symbol." | `TAKE_PROFIT_LIMIT` is not enabled on the symbol |
| "Price\* QTY is zero or less." | `price`\* `quantity` is too low |
| "IcebergQty exceeds QTY." | `icebergQty` must be less than the order quantity |
| "This action disabled is on this account." | Contact customer support; some actions have been disabled on the account. |
| "Unsupported order combination" | The `orderType`, `timeInForce`, `stopPrice`, and/or `icebergQty` combination isn't allowed. |
| "Order would trigger immediately." | The order's stop price is not valid when compared to the last traded price. |
| "Cancel order is invalid. Check origClOrdId and orderId." | No `origClOrdId` or `orderId` was sent in. |
| "Order would immediately match and take." | `LIMIT_MAKER` order type would immediately match and trade, and not be a pure maker order. |

## -9xxx Filter failures

| Error message | Description |
| :--- | :--- |
| "Filter failure: PRICE\_FILTER" | `price` is too high, too low, and/or not following the tick size rule for the symbol. |
| "Filter failure: LOT\_SIZE" | `quantity` is too high, too low, and/or not following the step size rule for the symbol. |
| "Filter failure: MIN\_NOTIONAL" | `price`\* `quantity` is too low to be a valid order for the symbol. |
| "Filter failure: MAX\_NUM\_ORDERS" | Account has too many open orders on the symbol. |
| "Filter failure: MAX\_ALGO\_ORDERS" | Account has too many open stop loss and/or take profit orders on the symbol. |
| "Filter failure: BROKER\_MAX\_NUM\_ORDERS" | Account has too many open orders on the broker. |
| "Filter failure: BROKER\_MAX\_ALGO\_ORDERS" | Account has too many open stop loss and/or take profit orders on the broker. |
| "Filter failure: ICEBERG\_PARTS" | Iceberg order would break into too many parts; icebergQty is too small. |

