# Errors

> `error` object

```json
{
  "returncode" : 400,
  "detail":"LACK_OF_POC",
  "message":"BAD REQUEST",
  "userMessage":"Insufficient amount of POC."
}
```

returncode | message | detail | userMessage
---------- | ------- | ------- | ---------
200 | Modal closed | MODAL_CLOSED | Modal closed.
400 | Bad request<br> ex) When clients send like below - wrong parameters and/or its value, - missing required parameters | MISSING_PARAMETER | 
 | | WRONG_PARAMS_VALUE | Please check your request and try it again.
 | | LACK_OF_POC | Insufficient amount of POC.
 | | EMAIL_IS_ALREADY_IN_USE | An account with this email is already in use.
 | | WRONG_SHOP_ITEM | The item could not be found in the shop.
 | | WRONG_ID_OR_PASSWORD | Invalid ID or password.
 | | WRONG_CURRENT_PASSWORD | Current password is incorrect.
 | | WRONG_FILE_EXTENSION | Wrong file extension.
 | | WRONG_USER_INFO_OR_OTP | Could not login because of wrong user info.
 | | NEED_AGREEMENT_PACOIN | Verification is required to use POC.
 | | UNKNOWN_USER_ITEM | It's an unknown user item.
 | | UNAVAILABLE_USER_ITEM | The item is unavailable.
 | | WRONG_PASSWORD | Invalid ID or password.
401 | Unauthorized<br> Player needs to login.<br> ex) - Valid session time is over. <br>- Player signed out.<br> - Player is not signed in.<br> - disabled account | UNKNOWN_USER | Unknown user.
 | | DISABLED_ACCOUNT | This account has been disabled.
 | | SESSION_EXPIRED | Session has expired.
429 | Too many request | TOO_MANY_SIGN_UP_WITH_SAME_IP | You can not create a PA Account on your current IP address.
500 | Server error<br> ex) server is not available, unknown error, etc | SYSTEM_ERROR | Server error has occurred.
 | | CAN_NOT_GET_USER_POC |  Server error has occurred.
 | | POC_SERVER_DID_NOT_RESPONSE |  Server error has occurred.
 | | CAN_NOT_REGISTER_TO_BLOCKCHAIN |  Server error has occurred.
502 | Bad gateway | BAD_GATEWAY | Server error has occurred.
503 | Service unavailable : ex) timeout, connection lost | SERVICE_UNAVAILABLE | Service unavailable. 
505 | Unknown<br> Unknown error | UNKNOWN | Unknown error has occurred.<br> Please try it later.
 | | FAILED_TO_UPDATE_USER_DATA | Save failed. Please try it again.
 | | ETC<br> When message is delivered from another server. The message varies.<br> Format : “ETC : (a message from another server)” <br>ex) “ETC : error on loadAccount“


