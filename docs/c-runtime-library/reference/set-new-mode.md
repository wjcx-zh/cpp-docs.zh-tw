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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: f3635d462d2c7438ce985d74ff347120c02c82e0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920094"
---
# <a name="_set_new_mode"></a>_set_new_mode

設定**malloc**的新處理常式模式。

## <a name="syntax"></a>語法

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>參數

*newhandlermode*<br/>
**Malloc**的新處理常式模式;有效值為0或1。

## <a name="return-value"></a>傳回值

傳回先前針對**malloc**所設定的處理常式模式。 傳回值1表示在無法配置記憶體時， **malloc**先前呼叫了新的處理常式常式;傳回值為0時，表示它不是。 如果*newhandlermode*引數不等於0或1，則會傳回-1。

## <a name="remarks"></a>備註

C++ **_set_new_mode** 函式會設定 [malloc](malloc.md) 的新處理常式模式。 新的處理常式模式指出，在失敗時， **malloc**是否會呼叫[_set_new_handler](set-new-handler.md)所設定的新處理常式常式。 根據預設， **malloc**不會在失敗時呼叫新的處理常式常式來配置記憶體。 您可以覆寫此預設行為，如此一來，當**malloc**無法配置記憶體時， **malloc**會呼叫新的處理常式，其方式會與**新**的運算子在因相同原因而失敗時所執行的相同。 如需詳細資訊，請參閱《C++ 語言參考》** 中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md) 運算子。 若要覆寫預設值，請及早在程式中呼叫：

```cpp
_set_new_mode(1);
```

，或使用 Newmode.obj 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。

這個函式會驗證其參數。 如果*newhandlermode*不是0或1，則函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， <strong>_set_new_mode</strong>會傳回-1，並將**errno**設定`EINVAL`為。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[受](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
