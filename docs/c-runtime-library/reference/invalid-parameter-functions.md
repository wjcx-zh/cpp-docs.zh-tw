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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0f0a3ea3e1f2e43d53650b4017905c696269ce20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343935"
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

*運算式*<br/>
表示原始程式碼參數運算式不是有效的字串。

*function_name*<br/>
呼叫此處理常式的函式名稱。

*file_name*<br/>
呼叫處理常式的原始程式碼檔。

*line_number*<br/>
呼叫處理常式的原始程式碼行號。

*保留*<br/>
未使用的。

## <a name="return-value"></a>傳回值

這些函式不會傳回值。 **_invalid_parameter_noinfo_noreturn**和 **_invoke_watson**函數不返回到調用方,在某些情況下 **,_invalid_parameter**和 **_invalid_parameter_noinfo**可能無法返回到調用方。

## <a name="remarks"></a>備註

當無效參數傳遞至 C 執行階段程式庫函式時，程式庫函式會呼叫「無效的參數處理常式」**，此函式可由程式設計師指定其可以做的事情。 例如，它可以將問題回報給使用者、寫入記錄檔、開啟偵錯工具、終止程式，或不執行任何動作。 如果程式者未指定任何函數,則呼叫預設處理程式 **_invoke_watson**。

默認情況下,當在調試代碼中識別無效參數時,CRT 庫函數使用詳細參數調用函數 **_invalid_parameter。** 在非調試代碼中,調用 **_invalid_parameter_noinfo**函數,該函數使用空參數調用 **_invalid_parameter**函數。 如果非調試CRT庫函數需要程式終止,則調用 **_invalid_parameter_noinfo_noreturn**函數,該函數使用空參數調用 **_invalid_parameter**函數,然後調用 **_invoke_watson**函數以強制程式終止。

**_invalid_parameter**函數檢查是否已設置使用者定義的無效參數處理程式,如果是,則調用它。 例如，如果使用者定義的執行緒區域處理常式經由目前的執行緒對 [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 進行呼叫而設定，則會呼叫它，然後傳回函式。 否則，如果使用者定義的全域無效的參數處理常式是經由呼叫 [set_invalid_parameter_handle](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 而設定，則會呼叫它，然後傳回函式。 否則,將調用預設處理程式 **_invoke_watson。** **_invoke_watson**的默認行為是終止程式。 使用者定義的處理常式可能會終止或傳回。 我們建議您，除非確定可復原，否則使用者定義的處理常式應終止程式。

當調用預設處理程式 **_invoke_watson**時,如果處理器支援[__fastfail](../../intrinsics/fastfail.md)操作,則使用**FAST_FAIL_INVALID_ARG**參數調用該處理程式,並且進程將終止。 否則，就會引發快速失敗例外狀況，這可以附加的偵錯工具來攔截。 如果允許進程繼續,則使用**STATUS_INVALID_CRUNTIME_PARAMETER**的異常代碼狀態調用 Windows**終止進程**函數將終止該進程。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|------------------|
|**_invalid_parameter,** **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[參數驗證](../../c-runtime-library/parameter-validation.md)<br/>
