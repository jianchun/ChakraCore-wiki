Write JavascriptString value into Utf8 string buffer
### Syntax 
```
CHAKRA_API
       JsCopyStringUtf8(
        _In_ JsValueRef value,
        _Out_opt_ uint8_t* buffer,
        _In_ size_t bufferSize,
        _Out_opt_ size_t* written);
```
### Parameters 
* __value__: JavascriptString value
* __buffer__: Pointer to buffer
* __bufferSize__: Buffer size
* __written__: Total number of characters written

### Return Value 
The code **JsNoError** if the operation succeeded, a failure code otherwise.
### Remarks 
When size of the `buffer` is unknown, `buffer` argument can be nullptr.
In that case, `written` argument will return the length needed.

When start is out of range or < 0, returns JsErrorInvalidArgument
and `written` will be equal to 0. If calculated length is 0 (It can be due to string length or `start`
and length combination), then `written` will be equal to 0 and call
returns JsNoError.