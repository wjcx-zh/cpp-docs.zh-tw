---
title: "_invalid_parameter、_invalid_parameter_noinfo、_invalid_parameter_noinfo_noreturn、_invoke_watson | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- CORECRT/_invalid_parameter
- _invalid_parameter
- CORECRT/_invalid_parameter_noinfo
- _invalid_parameter_noinfo
- CORECRT/_invalid_parameter_noinfo_noreturn
- _invalid_parameter_noinfo_noreturn
- CORECRT/_invoke_watson
- _invoke_watson
ms.assetid: a4d6f1fd-ce56-4783-8719-927151a7a814
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 49ae87567cd311e271a0ab50d7112a4a8f0c1b4a
ms.lasthandoff: 02/24/2017

---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter、_invalid_parameter_noinfo、_invalid_parameter_noinfo_noreturn、_invoke_watson
C 執行階段程式庫使用這些函式處理傳遞至 CRT 程式庫函式的無效參數。 您的程式碼也可以使用這些函式，以支援預設或自訂處理無效參數。

## <a name="syntax"></a>語法
```
extern "C" void __cdecl 
_invalid_parameter(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);  

extern "C" void __cdecl 
_invalid_parameter_noinfo(void);  

extern "C" __declspec(noreturn) void __cdecl 
_invalid_parameter_noinfo_noreturn(void);  

extern "C" __declspec(noreturn) void __cdecl 
_invoke_watson(  
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);
```

## <a name="return-value"></a>傳回值
這些函式不會傳回值。 `_invalid_parameter_noinfo_noreturn` 和 `_invoke_watson` 函式不會傳回至呼叫者，且在某些情況下，`_invalid_parameter` 和 `_invalid_parameter_noinfo` 可能不會傳回至呼叫者。

## <a name="parameters"></a>參數
`expression`  
表示原始程式碼參數運算式不是有效的字串。

`function_name`  
呼叫此處理常式的函式名稱。

`file_name`  
呼叫處理常式的原始程式碼檔。

`line_number`  
呼叫處理常式的原始程式碼行號。

`reserved`  
未使用。

## <a name="remarks"></a>備註
當無效參數傳遞至 C 執行階段程式庫函式時，程式庫函式會呼叫「無效的參數處理常式」，此函式可由程式設計師指定其可以做的事情。 例如，它可以將問題回報給使用者、寫入記錄檔、開啟偵錯工具、終止程式，或不執行任何動作。 如果程式設計師沒有指定任何功能，則會呼叫預設處理常式 `_invoke_watson`。

根據預設，當偵錯程式碼識別出無效參數時，CRT 程式庫函式會使用 verbose 參數呼叫 `_invalid_parameter` 函式。 在非偵錯程式碼中，會呼叫 `_invalid_parameter_noinfo` 函式，其會呼叫使用空白參數的 `_invalid_parameter` 函式。 如果非偵錯 CRT 程式庫函式需要終止程式，會呼叫 `_invalid_parameter_noinfo_noreturn` 函式，其會呼叫使用空白參數的 `_invalid_parameter` 函式，並接著呼叫 `_invoke_watson` 函式以強制終止程式。

`_invalid_parameter` 函式檢查是否已設定使用者定義的無效的參數處理常式，且如果已設定，則呼叫它。 例如，如果使用者定義的執行緒區域處理常式經由目前的執行緒對 [set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 進行呼叫而設定，則會呼叫它，然後傳回函式。 否則，如果使用者定義的全域無效的參數處理常式是經由呼叫 [set_invalid_parameter_handle](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 而設定，則會呼叫它，然後傳回函式。 否則，呼叫預設的處理常式 `_invoke_watson`。 `_invoke_watson` 的預設行為是終止程式。 使用者定義的處理常式可能會終止或傳回。 我們建議您，除非確定可復原，否則使用者定義的處理常式應終止程式。 

當呼叫預設處理常式 `_invoke_watson` 時，如果處理器支援 [__fastfail](../../intrinsics/fastfail.md) 作業，則會使用 `FAST_FAIL_INVALID_ARG` 參數來叫用處理常式，並終止處理序。 否則，就會引發快速失敗例外狀況，這可以附加的偵錯工具來攔截。 如果允許處理序繼續，會使用例外狀況代碼狀態 `STATUS_INVALID_CRUNTIME_PARAMETER` 來呼叫 Windows`TerminateProcess` 函式，以進行終止。 

## <a name="requirements"></a>需求  
|函式|必要的標頭|  
|--------------|------------------|  
|`_invalid_parameter`, `_invalid_parameter_noinfo`, `_invalid_parameter_noinfo_noreturn`, `_invoke_watson`|\<corecrt.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)  
 [_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)  
 [參數驗證](../../c-runtime-library/parameter-validation.md)

