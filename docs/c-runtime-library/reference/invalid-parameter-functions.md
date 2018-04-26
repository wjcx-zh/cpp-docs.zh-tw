---
title: _invalid_parameter、_invalid_parameter_noinfo、_invalid_parameter_noinfo_noreturn、_invoke_watson | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: 7f7bd5efc49ed2836262e33e1fa302f59c327a6a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter、_invalid_parameter_noinfo、_invalid_parameter_noinfo_noreturn、_invoke_watson

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

*運算式*表示來源的程式碼參數運算式不是有效的字串。

*function_name*呼叫此處理常式的函式的名稱。

*file_name*其中呼叫此處理常式的原始程式碼檔。

*line_number*其中呼叫此處理常式的原始程式碼中的行號。

*保留*未使用。

## <a name="return-value"></a>傳回值

這些函式不會傳回值。 **_Invalid_parameter_noinfo_noreturn**和 **_invoke_watson**函式不會傳回給呼叫者，並在某些情況下， **_invalid_parameter**和 **_invalid_parameter_noinfo**可能不會傳回給呼叫者。

## <a name="remarks"></a>備註

當無效參數傳遞至 C 執行階段程式庫函式時，程式庫函式會呼叫「無效的參數處理常式」，此函式可由程式設計師指定其可以做的事情。 例如，它可以將問題回報給使用者、寫入記錄檔、開啟偵錯工具、終止程式，或不執行任何動作。 如果函式不程式設計人員，預設的處理常式，以指定 **_invoke_watson**，稱為。

根據預設，偵錯的程式碼中已識別無效的參數時 CRT 程式庫函式呼叫的函式 **_invalid_parameter**使用 verbose 參數。 在非偵錯程式碼， **_invalid_parameter_noinfo**函式呼叫，而它會呼叫 **_invalid_parameter**函式使用空白的參數。 如果非偵錯 CRT 程式庫函式需要程式終止 **_invalid_parameter_noinfo_noreturn**函式呼叫，而它會呼叫 **_invalid_parameter**函式使用空白參數，後面接著呼叫 **_invoke_watson**函式來強制程式終止。

**_Invalid_parameter**函式檢查是否已設定的使用者定義的無效參數處理常式，而且如果是，會呼叫它。 例如，如果使用者定義的執行緒區域處理常式經由目前的執行緒對 [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 進行呼叫而設定，則會呼叫它，然後傳回函式。 否則，如果使用者定義的全域無效的參數處理常式是經由呼叫 [set_invalid_parameter_handle](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 而設定，則會呼叫它，然後傳回函式。 否則，預設處理常式 **_invoke_watson**呼叫。 預設行為 **_invoke_watson**是終止程式。 使用者定義的處理常式可能會終止或傳回。 我們建議您，除非確定可復原，否則使用者定義的處理常式應終止程式。

當預設處理常式 **_invoke_watson**呼叫時，如果處理器支援[__fastfail](../../intrinsics/fastfail.md)作業，它會叫用使用的參數**FAST_FAIL_INVALID_ARG**並在處理序終止。 否則，就會引發快速失敗例外狀況，這可以附加的偵錯工具來攔截。 如果允許繼續處理程序，它就會終止由 Windows 呼叫**TerminateProcess**函式使用的例外狀況程式碼狀態**STATUS_INVALID_CRUNTIME_PARAMETER**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|------------------|
|**_invalid_parameter**， **_invalid_parameter_noinfo**， **_invalid_parameter_noinfo_noreturn**， **_invoke_watson**|\<corecrt.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[參數驗證](../../c-runtime-library/parameter-validation.md)<br/>
