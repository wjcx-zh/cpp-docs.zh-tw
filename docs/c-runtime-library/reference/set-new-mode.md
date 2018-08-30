---
title: _set_new_mode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_new_mode
apilocation:
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
apitype: DLLExport
f1_keywords:
- set_new_mode
- _set_new_mode
dev_langs:
- C++
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78e3d346bca087a6fd855e6428e6a53779cd7355
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202512"
---
# <a name="setnewmode"></a>_set_new_mode

設定新處理常式模式**malloc**。

## <a name="syntax"></a>語法

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>參數

*newhandlermode*<br/>
新處理常式模式**malloc**; 有效的值是 0 或 1。

## <a name="return-value"></a>傳回值

傳回上一個處理常式的模式組**malloc**。 傳回值 1 表示，無法配置記憶體**malloc**之前稱為 「 新的處理常式模式; 傳回值 0 表示不。 如果*newhandlermode*引數不等於 0 或 1，則會傳回-1。

## <a name="remarks"></a>備註

C++ **_set_new_mode** 函式會設定 [malloc](malloc.md) 的新處理常式模式。 新的處理常式模式會指出是否在失敗時， **malloc**就是呼叫所設定的新處理常式[_set_new_handler](set-new-handler.md)。 根據預設， **malloc**不會呼叫新的處理常式無法配置記憶體。 您可以覆寫此預設行為，讓，當**malloc**無法配置記憶體， **malloc**呼叫新的處理常式在相同方式來**新**運算子因當它失敗，相同的原因。 如需詳細資訊，請參閱《C++ 語言參考》中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md) 運算子。 若要覆寫預設值，請及早在程式中呼叫：

```cpp
_set_new_mode(1);
```

，或使用 Newmode.obj 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。

這個函式會驗證其參數。 如果*newhandlermode*不是 0 或 1，此函式會在將無效的參數處理常式中，做為叫用的任何項目中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行<strong>_set_new_mode</strong>會傳回-1 並將**errno**到`EINVAL`。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
