---
title: _set_new_mode
ms.date: 4/2/2020
api_name:
- _set_new_mode
- _o__set_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_new_mode
- _set_new_mode
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
ms.openlocfilehash: 3a27717d65714de54f477e4e2b3f243c4631fd8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332327"
---
# <a name="_set_new_mode"></a>_set_new_mode

設置**Malloc**的新處理程式模式。

## <a name="syntax"></a>語法

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>參數

*新處理常式模式*<br/>
**MALLoc**的新處理程式模式 ;有效值為 0 或 1。

## <a name="return-value"></a>傳回值

返回為**malloc**設置的上一個處理程式模式。 返回值 1 表示,在分配記憶體失敗時,malloc 以前調用了新的處理程式例程;否則 **,malloc**調用了新的處理程式例程。返回值 0 表示沒有。 如果*newhandlermode*參數不等於 0 或 1,則返回 -1。

## <a name="remarks"></a>備註

C++ **_set_new_mode** 函式會設定 [malloc](malloc.md) 的新處理常式模式。 新的處理程式模式指示在發生故障時 **,malloc**是否將調用[由 _set_new_handler](set-new-handler.md)設置的新處理程式例程。 默認情況下 **,malloc**不會在分配記憶體失敗時調用新的處理程式例程。 您可以重寫此預設行為,以便在**malloc**無法分配記憶體時 **,malloc**呼叫新處理程式例程的方式**與新運算符出於**相同原因失敗時相同的方式呼叫新處理程式例程。 如需詳細資訊，請參閱《C++ 語言參考》** 中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md) 運算子。 若要覆寫預設值，請及早在程式中呼叫：

```cpp
_set_new_mode(1);
```

，或使用 Newmode.obj 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。

這個函式會驗證其參數。 如果*newhandlermode*是除 0 或 1 以外的任何內容,則函數將調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行<strong>,_set_new_mode</strong>傳回 -1 並將**errno**`EINVAL`設定到 。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[自由](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
