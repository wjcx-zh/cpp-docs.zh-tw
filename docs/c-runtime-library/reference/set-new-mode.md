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
ms.openlocfilehash: 9b914e950fd94435768c355f327d3d48a653e0d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407141"
---
# <a name="setnewmode"></a>_set_new_mode

設定新處理常式模式**malloc**。

## <a name="syntax"></a>語法

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>參數

*newhandlermode*<br/>
針對新的處理常式模式**malloc**; 有效的值是 0 或 1。

## <a name="return-value"></a>傳回值

傳回前一個處理常式的模式組**malloc**。 傳回值為 1，表示無法配置記憶體， **malloc**之前呼叫新的處理常式; 傳回值 0 表示不一樣。 如果*newhandlermode*引數不等於 0 或 1，傳回-1。

## <a name="remarks"></a>備註

C++ **_set_new_mode** 函式會設定 [malloc](malloc.md) 的新處理常式模式。 新的處理常式模式指出是否在失敗時， **malloc**是新的處理常式呼叫所設定的[_set_new_handler](set-new-handler.md)。 根據預設， **malloc**不會呼叫新的處理常式在無法配置記憶體。 您可以覆寫此預設行為，讓，當**malloc**無法配置記憶體， **malloc**呼叫新的處理常式在相同的方式來**新**運算子會當它失敗基於相同原因。 如需詳細資訊，請參閱《C++ 語言參考》中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md) 運算子。 若要覆寫預設值，請及早在程式中呼叫：

```cpp
_set_new_mode(1);
```

，或使用 Newmode.obj 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。

這個函式會驗證其參數。 如果*newhandlermode*而不是 0 或 1，此函式做為叫用無效參數處理常式的任何項目述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行 **_ * * * set_new_mode**傳回-1，並設定**errno**至**EINVAL**。

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
