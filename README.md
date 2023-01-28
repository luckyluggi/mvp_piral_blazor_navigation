# Repro Steps
- `cd ./appshell` and run `npm i` and then `npm run build`
- `cd ../blazor-pilet` and run `dotnet build`
- `cd ../.piral~/blazor-pilet` and run `npm run start`

# Problem
- open `http://localhost:1234/home` in the browser
- open the browser dev tools
- click the `About` link to move to the about page
- you will see the following error in the dev tools:

# Error message
```
blazor.webassembly.js:1 Uncaught (in promise) Error: System.Text.Json.JsonException: The JSON value could not be converted to System.String. Path: $ | LineNumber: 0 | BytePositionInLine: 5.
 ---> System.InvalidOperationException: Cannot get the value of a token type 'False' as a string.
   at System.Text.Json.ThrowHelper.ThrowInvalidOperationException_ExpectedString(JsonTokenType tokenType)
   at System.Text.Json.Utf8JsonReader.GetString()
   at System.Text.Json.Serialization.Converters.StringConverter.Read(Utf8JsonReader& reader, Type typeToConvert, JsonSerializerOptions options)
   at System.Text.Json.Serialization.JsonConverter`1[[System.String, System.Private.CoreLib, Version=7.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e]].TryRead(Utf8JsonReader& reader, Type typeToConvert, JsonSerializerOptions options, ReadStack& state, String& value)
   at System.Text.Json.Serialization.JsonConverter`1[[System.String, System.Private.CoreLib, Version=7.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e]].ReadCore(Utf8JsonReader& reader, JsonSerializerOptions options, ReadStack& state)
   --- End of inner exception stack trace ---
   at System.Text.Json.ThrowHelper.ReThrowWithPath(ReadStack& state, Utf8JsonReader& reader, Exception ex)
   at System.Text.Json.Serialization.JsonConverter`1[[System.String, System.Private.CoreLib, Version=7.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e]].ReadCore(Utf8JsonReader& reader, JsonSerializerOptions options, ReadStack& state)
   at System.Text.Json.Serialization.JsonConverter`1[[System.String, System.Private.CoreLib, Version=7.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e]].ReadCoreAsObject(Utf8JsonReader& reader, JsonSerializerOptions options, ReadStack& state)
   at System.Text.Json.JsonSerializer.ReadCore[Object](Utf8JsonReader& reader, JsonTypeInfo jsonTypeInfo, ReadStack& state)
   at System.Text.Json.JsonSerializer.Read[Object](Utf8JsonReader& reader, JsonTypeInfo jsonTypeInfo)
   at System.Text.Json.JsonSerializer.Deserialize(Utf8JsonReader& reader, Type returnType, JsonSerializerOptions options)
   at Microsoft.JSInterop.Infrastructure.DotNetDispatcher.ParseArguments(JSRuntime jsRuntime, String methodIdentifier, String arguments, Type[] parameterTypes)
   at Microsoft.JSInterop.Infrastructure.DotNetDispatcher.InvokeSynchronously(JSRuntime jsRuntime, DotNetInvocationInfo& callInfo, IDotNetObjectReference objectReference, String argsJson)
   at Microsoft.JSInterop.Infrastructure.DotNetDispatcher.BeginInvokeDotNet(JSRuntime jsRuntime, DotNetInvocationInfo invocationInfo, String argsJson)
    at Object.endInvokeDotNetFromJS (http://localhost:1234/$pilet-api/0/_framework/blazor.webassembly.js:1:3549)
    at Object.Xt [as endInvokeDotNetFromJS] (http://localhost:1234/$pilet-api/0/_framework/blazor.webassembly.js:1:63231)
    at Object.Gt [as invokeJSFromDotNet] (http://localhost:1234/$pilet-api/0/_framework/blazor.webassembly.js:1:62728)
    at Object.Ii (http://localhost:1234/$pilet-api/0/_framework/dotnet.7.0.2.gr8o5rjjvv.js:5:71465)
    at _mono_wasm_invoke_js_blazor (http://localhost:1234/$pilet-api/0/_framework/dotnet.7.0.2.gr8o5rjjvv.js:14:103886)
    at wasm://wasm/00992bd6:wasm-function[313]:0x1d4d8
    at wasm://wasm/00992bd6:wasm-function[283]:0x1c906
    at wasm://wasm/00992bd6:wasm-function[221]:0xdff6
    at wasm://wasm/00992bd6:wasm-function[220]:0xce95
    at wasm://wasm/00992bd6:wasm-function[8115]:0x1a2195
endInvokeDotNetFromJS @ blazor.webassembly.js:1
Xt @ blazor.webassembly.js:1
Gt @ blazor.webassembly.js:1
Ii @ dotnet.7.0.2.gr8o5rjjvv.js:5
_mono_wasm_invoke_js_blazor @ dotnet.7.0.2.gr8o5rjjvv.js:14
$func313 @ 00992bd6:0x1d4d8
$func283 @ 00992bd6:0x1c906
$func221 @ 00992bd6:0xdff6
$func220 @ 00992bd6:0xce95
$func8115 @ 00992bd6:0x1a2195
$func2054 @ 00992bd6:0x85bba
$func2059 @ 00992bd6:0x86222
$func2086 @ 00992bd6:0x882e1
$mono_wasm_invoke_method_ref @ 00992bd6:0x9bd1
Module._mono_wasm_invoke_method_ref @ dotnet.7.0.2.gr8o5rjjvv.js:14
_Microsoft_AspNetCore_Components_WebAssembly__Microsoft_AspNetCore_Components_WebAssembly_Services_DefaultWebAssemblyJSRuntime_BeginInvokeDotNet @ _Microsoft_AspNetCore_Components_WebAssembly__Microsoft_AspNetCore_Components_WebAssembly_Services_DefaultWebAssemblyJSRuntime_BeginInvokeDotNet:29
beginInvokeDotNetFromJS @ blazor.webassembly.js:1
b @ blazor.webassembly.js:1
e.invokeMethodAsync @ blazor.webassembly.js:1
callNotifyLocationChanged @ index.js?updated=1674897613062:278
(anonym) @ index.js?updated=1674897613062:425
handler @ navigator_v5.js:68
(anonym) @ navigator_v5.js:13
commitHookEffectListMount @ react-dom.development.js:23150
commitPassiveMountOnFiber @ react-dom.development.js:24931
commitPassiveMountEffects_complete @ react-dom.development.js:24891
commitPassiveMountEffects_begin @ react-dom.development.js:24878
commitPassiveMountEffects @ react-dom.development.js:24866
flushPassiveEffectsImpl @ react-dom.development.js:27039
flushPassiveEffects @ react-dom.development.js:26984
(anonym) @ react-dom.development.js:26769
workLoop @ scheduler.development.js:266
flushWork @ scheduler.development.js:239
performWorkUntilDeadline @ scheduler.development.js:533
```