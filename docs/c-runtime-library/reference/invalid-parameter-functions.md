---
title: _invalid_parameter、_invalid_parameter_noinfo、_invalid_parameter_noinfo_noreturn、_invoke_watson
ms.date: 4/2/2020
api_name:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
- _o__invalid_parameter_noinfo
- _o__invalid_parameter_noinfo_noreturn
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 7138e9cb7381e4d40911054e1473536b6e639e2d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919827"
---
# <a name="_invalid_parameter-_invalid_parameter_noinfo-_invalid_parameter_noinfo_noreturn-_invoke_watson"></a>_invalid_parameter、_invalid_parameter_noinfo、_invalid_parameter_noinfo_noreturn、_invoke_watson

C 執行階段程式庫使用這些函式處理傳遞至 CRT 程式庫函式的無效參數。 您的程式碼也可以使用這些函式，以支援預設或自訂處理無效參數。

## <a name="syntax"></a>語法

```C
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

## <a name="parameters"></a>參數

*expression*<br/>
表示原始程式碼參數運算式不是有效的字串。

*function_name*<br/>
呼叫此處理常式的函式名稱。

*file_name*<br/>
呼叫處理常式的原始程式碼檔。

*line_number*<br/>
呼叫處理常式的原始程式碼行號。

*留*<br/>
未使用的。

## <a name="return-value"></a>傳回值

這些函式不會傳回值。 **_Invalid_parameter_noinfo_noreturn**和 **_invoke_watson**函數不會傳回給呼叫者，在某些情況下， **_invalid_parameter**和 **_invalid_parameter_noinfo**可能不會傳回給呼叫者。

## <a name="remarks"></a>備註

當無效參數傳遞至 C 執行階段程式庫函式時，程式庫函式會呼叫「無效的參數處理常式」**，此函式可由程式設計師指定其可以做的事情。 例如，它可以將問題回報給使用者、寫入記錄檔、開啟偵錯工具、終止程式，或不執行任何動作。 如果程式設計人員未指定任何函式，則會呼叫預設處理常式 **_invoke_watson**。

根據預設，當在 debug 程式碼中識別出不正確參數時，CRT 程式庫函式會使用 verbose 參數來呼叫函數 **_invalid_parameter** 。 在非 debug 程式碼中，會呼叫 **_invalid_parameter_noinfo**函式，此函式會使用空的參數來呼叫 **_invalid_parameter**函數。 如果非 debug CRT 程式庫函式需要程式終止，則會呼叫 **_invalid_parameter_noinfo_noreturn**函式，此函式會使用空白參數呼叫 **_invalid_parameter**函式，然後再呼叫 **_invoke_watson**函式來強制終止程式。

**_Invalid_parameter**函式會檢查是否已設定使用者定義的無效參數處理常式，如果是，則會呼叫它。 例如，如果使用者定義的執行緒區域處理常式經由目前的執行緒對 [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 進行呼叫而設定，則會呼叫它，然後傳回函式。 否則，如果使用者定義的全域無效的參數處理常式是經由呼叫 [set_invalid_parameter_handle](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 而設定，則會呼叫它，然後傳回函式。 否則，會呼叫預設處理常式 **_invoke_watson** 。 **_Invoke_watson**的預設行為是終止程式。 使用者定義的處理常式可能會終止或傳回。 我們建議您，除非確定可復原，否則使用者定義的處理常式應終止程式。

當呼叫預設處理常式 **_invoke_watson**時，如果處理器支援[__fastfail](../../intrinsics/fastfail.md)作業，則會使用**FAST_FAIL_INVALID_ARG**的參數來叫用，而且進程會終止。 否則，就會引發快速失敗例外狀況，這可以附加的偵錯工具來攔截。 如果允許繼續執行，則會使用**STATUS_INVALID_CRUNTIME_PARAMETER**的例外狀況代碼狀態呼叫 Windows **TerminateProcess**函數來終止進程。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|------------------|
|**_invalid_parameter**、 **_invalid_parameter_noinfo**、 **_invalid_parameter_noinfo_noreturn**、 **_invoke_watson**|\<corecrt.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[參數驗證](../../c-runtime-library/parameter-validation.md)<br/>
