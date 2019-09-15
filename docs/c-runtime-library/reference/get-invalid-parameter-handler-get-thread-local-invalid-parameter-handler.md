---
title: _get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler
ms.date: 11/04/2016
api_name:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: 534590fed77fe06149db892d98ba0e555297ac7c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955824"
---
# <a name="_get_invalid_parameter_handler-_get_thread_local_invalid_parameter_handler"></a>_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler

取得 CRT 偵測到無效的引數時，會呼叫的函式。

## <a name="syntax"></a>語法

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>傳回值

目前已設定的無效的參數處理常式函式的指標，或如果未設定，則為 Null 指標。

## <a name="remarks"></a>備註

**_Get_invalid_parameter_handler**函數會取得目前設定的全域無效參數處理常式。 如果未設定任何全域無效的參數處理常式，它會傳回 Null 指標。 同樣地， **_get_thread_local_invalid_parameter_handler**會取得其所呼叫之執行緒的目前線程本機無效參數處理常式，如果未設定處理常式，則為 null 指標。 如需有關如何設定全域和執行緒區域無效的參數處理常式的資訊，請參閱 [_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)。

傳回的無效的參數處理常式函式指標具有下列類型︰

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

如需無效的參數處理常式的詳細資訊，請參閱 [_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 中的原型。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_invalid_parameter_handler**、 **_get_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib> 或 \<stdlib.h>|

**_Get_invalid_parameter_handler**和 **_get_thread_local_invalid_parameter_handler**函式是 Microsoft 特有的功能。 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[CRT 函式的安全性增強版本](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
